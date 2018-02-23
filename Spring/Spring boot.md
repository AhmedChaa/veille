##Advantages
- Faciliter la gestion de dépendances
- Auto Configuration (DispatcherServlet, ResourceHadlers, MessageSource, Log, ...) avec des paramètres par défaut
- Détection de dépendances automatique : Data Source par exemple :
    * La présence des jars H2 ou HSQL dans le classPath, il crée une Data Source avec le EntityManager correspondant et tt
- Embedded Servlet Container (Tomcat, ou Jetty) intégrés 
- Production-Ready metrics, health checks, externalized configs, ...

- Microservices :

    * https://www.3pillarglobal.com/insights/building-a-microservice-architecture-with-spring-boot-and-docker-part-i
    * https://spring.io/blog/2015/07/14/microservices-with-spring
    * https://dzone.com/articles/spring-boot-creating

## Disadvantages
- Si on a du code legacy qui est contradiction avec les starters
- Automatique configuration peut être un sérieux problème si on maîtrise pas les confs
- Augmente la taille du binaire en sortie