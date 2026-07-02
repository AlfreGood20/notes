# Spring Security

Spring Security es un marco poderoso y flexible diseñado para proporcionar autenticación, autorización y otras características de seguridad en aplicaciones Java. Su arquitectura está basada en una serie de componentes modulares que interactúan entre sí para garantizar la protección de los recursos de la aplicación.

Esquema de ilustracion de filtro:

![ilustracion](https://careers.edicomgroup.com/wp-content/uploads/2025/10/Slide15-1.jpg)

## Dependencia
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

## Configuraciones

```java

@Configuration
public class SecurityConfig{

	private final CustomAuthenticationEntryPoint autehnticationEntryPoint;
	private final CustomAccessDeniedHandler accessDeniedHandler;

	@Bean
	public SecurityFilterChain filterChain(httpSecurity http) throws Exception {
		http
			// Desactiva el csrf
			.csrf(csrf -> csrf.disnable())

			// Tipos de estados
			// - STATELESS -> Sin estado
			// - IF_REQUIRED -> Con estado
            .sessionManagement(session -> session
				.sessionCreationPolicy(SessionCreationPolicy.STATELESS))

			// Manejar error 401 personalizado
			.httpBasic(httpBasic -> httpBasic
				.authenticationEntryPoint(authenticationEntryPoint)
			)

			// Manejar error 403 personalizado
			.exceptionHandling(exh -> exh
				.accessDeniedHandler(accessDeniedHandler));

			// Manejo de autorizacion y roles
			.authorizeHttpRequests(requests -> requests

				//El uso de hasRole se usa para indicar los roles de una ruta
				//Puede tener muchos roles

				.requestMatchers("/user/**").hasAnyRole('ROLE_USER','ROLE_ADMIN')
				
				//Solo un rol puede tener
				.requestMatchers("/admin/**").hasRole('ROLE_ADMIN')
				
				//Ruta public para cualquiera
				.requestMatchers("/public/**").permitAll()
				
				//Nadien puede entrar
				.requestMatchers("/documents-v1").denyAll()

				// Si esta autenticado no podra ingresar a esta ruta
				.requestMathers("/register").anonymous()

				// El uso de hasAuthority se usa para diferentes permisos de una ruta
				.requestMathers(httpMethod.GET,"users/**").hasAuthority('READ')
				.requestMathers(httpMethod.POST,"users/").hasAuthority('WRITE')
				.requestMathers(httpMethod.PUT, "users/**").hasAuthority('UPDATE')
				.requestMathers(httpMethod.DELETE, "users/**").hasAuthority('DELETE')

				// Igual puede tener muchos persmisos una ruta
				.requestMathers("/Reports").hasAnyAuthority('READ','IMPORT')

				//Las demas rutas necesitara autenticacion
				.anyRequest().authenticated()
			)
			
			;

		return http.build();
	}
}
```

## Manejo de erres 401 y 403

### Error 401 (Recurso no autorizado)
La interfaz AuthenticationEntryPoint es la responsable de manejar los intentos de acceso no autenticados, decidiendo cómo responder cuando alguien accede a la API sin autenticación. Para crear una implementación personalizada de AuthenticationEntryPoint es necesario sobrescribir el método commence().

```java
@Component
public class CustomAuthenticationEntryPoint implements AuthenticationEntryPoint {

	@Override
	public void commence(HttpServletRequest request, HttpServletResponse response, AuthenticationException authException) throws IOException {
		// LOGICA Y MENSAJE DE 401
	}
}
```

### Error 403 (Recurso no permitido)
AccessDeniedHandler es una interfaz en Spring Security que se utiliza para manejar situaciones en las que un usuario intenta acceder a un recurso protegido sin los permisos necesarios. Cuando ocurre un error de acceso denegado (403 Forbidden), esta interfaz permite personalizar la respuesta que se envía al cliente. En este caso, un AccessDeniedHandler personalizado puede crearse sobrescribiendo el método handle() y configurarse utilizando exceptionHandling().

```java
@Component
public class CustomAccessDeniedHandler implements AccessDeniedHandler {
	
	@Override
	public void handle(HttpServletRequest request, HttpServletResponse response, AccessDeniedException accessDeniedException) throws IOException {
		// LOGICA Y MENSAJE 403
	}
}
```


