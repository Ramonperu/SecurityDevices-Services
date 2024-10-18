# Security Devices & Services

## FIREWALL

Un firewall es un dispositivo o software que supervisa y controla el tráfico de red entrante y saliente según reglas de seguridad predeterminadas

### **Propiedades mas comunes** 

- **Filtrado de Paquetes (Packet Filtering)**: Inspecciona cada paquete de datos que pasa a través de la red y lo compara con un conjunto de reglas definidas. Solo permite el tráfico que cumple con los criterios establecidos (como origen, destino, puerto, protocolo, etc.).
- **Filtrado de Aplicaciones (Application Filtering)**: Permite o bloquea el acceso a aplicaciones específicas. Puede identificar y filtrar tráfico basado en aplicaciones (como navegación web, correo electrónico, etc.).
- **Gestión de Políticas**: Los firewalls permiten configurar y aplicar políticas de seguridad personalizadas para redes, subredes, usuarios, dispositivos y más. Estas políticas determinan cómo se manejan las conexiones entrantes y salientes.
- **Red de Perímetro**: Actúan como una barrera protectora entre una red interna confiable y redes externas no confiables, como internet. Protegen los recursos internos de amenazas externas.
- **Registros y Monitorización (Logging & Monitoring)**: Proporcionan registros detallados del tráfico de red, alertas y auditoría de eventos de seguridad, lo que permite identificar patrones inusuales y ataques potenciales.

**Beneficios**

- **Protección contra accesos no autorizados**: Bloquea el tráfico no deseado o sospechoso, impidiendo que actores maliciosos accedan a la red interna.
- **Gestión centralizada de políticas de seguridad**: Permite a los administradores aplicar reglas y restricciones en diferentes segmentos de la red de manera eficiente.
- **Mitigación de ataques comunes**: Bloquea ataques como **DDoS (Denegación de Servicio Distribuida)**, **spoofing** (suplantación de identidad) y **escaneos de puertos** que buscan vulnerabilidades en una red.
- **Registro y auditoría de eventos de seguridad**: Los firewalls mantienen un registro de los eventos que ocurren en la red.
- **Segmentación de redes**: Permite dividir la red en zonas o subredes, de forma que los diferentes segmentos de la red puedan ser protegidos con reglas específicas, lo que aísla los problemas de seguridad y reduce los riesgos.
- **Cumplimiento de normativas**: Ayuda a las organizaciones a cumplir con regulaciones y estándares de seguridad, como PCI-DSS, ISO/IEC 27001, HIPAA, entre otros.

**Limitaciones**

- **No protegen contra amenazas internas**: Si la amenaza es interna el firewall no puede ofrecer protección
- **No puede detectar malware/phishing avanzado**: Se necesitan otras herramientas como sistemas de detección de intrusiones (IDS) o antivirus.
- **Configuración compleja**: Si no se configura correctamente puede ser ineficaz o incluso contraproducente, dejando brechas en la seguridad que podrían ser explotadas.
- **Falso sentido de seguridad**: Un firewall debe formar parte de una estrategia de defensa en profundidad que incluya otras capas de seguridad como cifrado, autenticación y sistemas de detección de intrusiones.
- **Rendimiento**: Puede convertirse en un cuello de botella para el tráfico de red si la configuracion esta sobrecargada, lo que impacta el rendimiento general de la red.
- **No filtra tráfico cifrado**: No pueden inspeccionar el contenido de los datos cifrados sin descomprimir la capa de cifrado (como TLS/SSL), lo que puede dejar ciertas amenazas ocultas dentro de dicho tráfico.

### Tipos de Firewalls

#### **Firewall Stateless (Sin Estado)**

Toma decisiones sobre el tráfico de red basándose únicamente en la información contenida en cada paquete de datos de forma independiente, sin considerar el contexto de una conexión en curso.

**Características clave:**

- **Filtrado de paquetes básico**: Evalúa cada paquete de manera individual, observando atributos como la dirección IP de origen, la dirección IP de destino, el puerto, el protocolo y las reglas predefinidas en la tabla de filtrado.
- **No mantiene el estado de la conexión**: No sigue ni almacena el estado de una sesión de red. No distingue entre el tráfico que pertenece a una conexión existente y el tráfico malicioso que intenta establecer una nueva conexión.

<img align="center" src="/img/4ºimagenn.PNG"  />

#### **Firewall Stateful (Con Estado)**

Rastrea el **estado** de las conexiones activas y toma decisiones de filtrado basadas en el contexto de esas conexiones. Analiza no solo la cabecera de los paquetes, sino también la secuencia en la que se envían.

**Características clave:**

- **Mantiene el estado de la conexión**: Los firewalls stateful mantienen un registro de todas las conexiones activas que pasan a través del firewall. Monitorea el tráfico en tiempo real para asegurarse de que los paquetes están asociados a conexiones legítimas.
- **Decisiones basadas en contexto**: Examina el tráfico en el contexto de una conexión ya establecida, por lo que solo permite paquetes que correspondan a sesiones válidas y bloquea aquellos que intenten iniciar nuevas conexiones de manera no autorizada.

<img align="center" src="/img/5ºimagenn.PNG"  />

#### **Application Gateway Firewall (Firewall de Nivel de Aplicación)**

Conocido como **firewall de proxy** o **firewall de capa 7**(mayoritariamente trabaja en esta capa), este tipo de firewall trabaja a nivel de **aplicación**, es decir, a la capa más alta del modelo OSI, y es capaz de filtrar el tráfico basado en aplicaciones específicas (HTTP, FTP, DNS, etc.).

**Características clave:**

- **Inspección profunda de paquetes (DPI)**: El firewall analiza no solo las cabeceras de los paquetes, sino también el contenido de los mismos, a nivel de aplicación. Esto permite detectar comportamientos anómalos en el uso de aplicaciones.
- **Actúa como proxy**: Puede actuar como un intermediario entre el usuario y el servidor. Todos los paquetes deben pasar por el proxy, lo que le permite filtrar tráfico sospechoso basado en el comportamiento de la aplicación.
- **Control granular de aplicaciones**: Ofrece un control más detallado sobre qué aplicaciones pueden comunicarse a través de la red, permitiendo o denegando el tráfico según las políticas de seguridad establecidas.

**Next-Generation Firewall (NGFW) - Firewall de Próxima Generación**

Son una evolución de los firewalls tradicionales, ya sean stateful o stateless. Combinan las funcionalidades de un firewall de estado con capacidades avanzadas, como **detección de intrusiones (IDS/IPS)**, **filtrado de contenido**, y **protección frente a malware**. Trabajan a nivel de red y de aplicación.

**Características clave:**

- **Inspección profunda de paquetes (DPI)**: Similar a los firewalls de aplicación, los NGFW inspeccionan el contenido de los paquetes a nivel de aplicación (capa 7 del modelo OSI), permitiendo un control granular del tráfico.
- **Integración con sistemas de prevención de intrusiones (IPS)**: Los NGFW no solo identifican ataques, sino que también pueden prevenirlos en tiempo real.
- **Filtrado basado en identidad y comportamiento**: En lugar de basar las políticas solo en IPs y puertos, los NGFW pueden aplicar políticas según la identidad del usuario, los roles dentro de la organización o el comportamiento observado.
- **Control de aplicaciones**: Ofrecen control sobre aplicaciones específicas (Facebook, YouTube, Skype, etc.) y permiten aplicar políticas específicas para cada una.

#### Comparativa de los tipos de firewalls:

| **Tipo de Firewall**       | **Nivel de Protección** | Beneficios                                         | **Limitaciones**                                      |
| -------------------------- | ----------------------- | -------------------------------------------------- | ----------------------------------------------------- |
| **Stateless**              | Bajo                    | Rápido, sencillo de configurar                     | Menor seguridad, no protege contra ataques complejos  |
| **Stateful**               | Medio                   | Seguridad mejorada, seguimiento de conexiones      | Mayor uso de recursos, vulnerable a ataques avanzados |
| **Application Gateway**    | Alto                    | Control granular, protege aplicaciones específicas | Más lento, requiere más recursos y configuración      |
| **Next-Generation (NGFW)** | Muy alto                | Protección avanzada contra amenazas modernas       | Coste elevado, alto consumo de recursos               |

------

## Arquitecturas típicas de seguridad

### Red Pública/Privada

Su propósito es separar el tráfico **público** (internet) del tráfico **privado** (red interna). Los firewalls juegan un papel crucial aquí.

**Características clave:**

- **Red Pública (Internet)**: Es la parte de la red que está expuesta al mundo exterior. 
- **Red Privada (LAN - Local Area Network)**: Esta es la red interna de la organización, que contiene sistemas sensibles, como servidores de bases de datos, dispositivos de almacenamiento y usuarios internos. No debería ser accesible desde internet sin medidas de seguridad estrictas.
- **Firewall perimetral**: Se ubica entre la red pública y la privada, filtrando el tráfico. El firewall en esta arquitectura tiene la función de bloquear accesos no autorizados desde la red pública hacia la red privada.

<img align="center" src="/img/1ºimagenn.PNG"  />

**Beneficios:**

- **Aislamiento claro entre lo público y lo privado**, lo que limita la exposición directa de activos internos a internet.
- **Control simple** con reglas de firewall basadas en IP, puertos y protocolos para proteger los sistemas internos.

**Limitaciones:**

- Puede ser insuficiente para redes más complejas o escenarios con múltiples servicios públicos (servidores web, correo, etc.).
- No hay segmentación adicional dentro de la red privada, lo que significa que si un atacante entra, podría moverse libremente dentro de la LAN.

### Zona Desmilitarizada (DMZ)

La arquitectura de seguridad con **DMZ (Demilitarized Zone)** es más avanzada y comúnmente usada cuando se necesita publicar servicios hacia internet (como servidores web o de correo) sin exponer la red privada.

**Características clave:**

- **DMZ**: Es una subred (zona intermedia) ubicada entre la red pública y la red privada. Los servicios que requieren acceso desde internet (por ejemplo, servidores web, servidores de correo, etc.) se colocan en esta zona. La idea es que, incluso si un atacante compromete un servidor en la DMZ, no podrá acceder fácilmente a la red privada.
- **Firewall externo**: Ubicado entre internet y la DMZ, controla el tráfico entrante desde la red pública hacia los servicios en la DMZ.
- **Firewall interno**: Ubicado entre la DMZ y la red privada. Este firewall tiene reglas más restrictivas para evitar que el tráfico malicioso de la DMZ alcance los sistemas críticos en la red privada.

<img align="center" src="/img/2ºimagenn.PNG"  />

**Beneficios:**

- **Segmentación de servicios públicos**: Los servicios que necesitan ser accesibles desde internet (como servidores web o FTP) se colocan en la DMZ, reduciendo el riesgo de que un ataque comprometa la red interna.
- **Doble protección**: Al disponer de dos firewalls.
- **Mitigación de ataques**: Si un atacante compromete la DMZ, la red interna permanece protegida por el segundo firewall.

**Limitaciones:**

- **Gestión más compleja** debido a la necesidad de mantener múltiples políticas de firewall y la configuración de una zona adicional.
- **Mayor coste**: Se requiere más infraestructura y recursos (servidores en la DMZ, más firewalls, etc.).



### Firewalls de Políticas Basadas en Zonas

Son una arquitectura en la que las políticas de seguridad no se aplican solo a nivel de red pública y privada, sino que se crean zonas de seguridad lógicas dentro de la red para controlar mejor el tráfico y la comunicación entre diferentes segmentos de la red.

**Características clave:**

- **Zonas de seguridad**: Una zona es un grupo lógico de interfaces o subredes que comparten la misma política de seguridad. Por ejemplo, puedes tener una zona para servidores, una para usuarios internos, una para la DMZ y otra para invitados.
- **Políticas basadas en zonas:** En lugar de aplicar políticas de firewall en interfaces de red individuales, las políticas se aplican entre zonas. Esto facilita la administración de las reglas porque puedes definir políticas de seguridad globales entre diferentes zonas. Ejemplo:
  - **Política Zona A -> Zona B**: Permitir tráfico HTTP/HTTPS.
  - **Política Zona C -> Zona A**: Bloquear todo el tráfico.
- **Firewalls de nueva generación**: Muchos de los firewalls modernos, también llamados firewalls de próxima generación (NGFW, Next-Generation Firewall), utilizan políticas basadas en zonas para una administración más eficiente y granular.

<img align="center" src="/img/3ºimagenn.PNG"  />

**Beneficios:**

- **Segmentación más precisa**: Permite un mayor control y segmentación de la red. Se pueden definir zonas por función (servidores, usuarios, invitados, etc.) y crear reglas específicas para cada flujo de tráfico entre esas zonas.
- **Mayor flexibilidad**: Las políticas se pueden adaptar fácilmente a nivel de zona en lugar de cambiar reglas individuales en múltiples interfaces.
- **Mayor seguridad al limitar por segmentos.**

**Limitaciones:**

- **Requiere mayor planificación**: Es necesario definir correctamente las zonas y las políticas de tráfico, lo que puede ser complejo si no se entiende bien la estructura de la red y el flujo de datos.
- **Sobrecarga administrativa**: Si la red tiene demasiadas zonas y políticas, la administración puede volverse difícil de manejar sin herramientas adecuadas.

------

## Servicios de Seguridad

### **Access Control Lists (ACLs)**

Son reglas configuradas en routers o firewalls que permiten o bloquean el tráfico basándose en parámetros como dirección IP, puertos o protocolos.

**Beneficios:**

- Control granular sobre el tráfico de red.
- Refuerzan la seguridad al restringir el acceso a recursos críticos.
- Sencillas de implementar en dispositivos de red.

**Limitaciones:**

- No ofrecen protección avanzada contra ataques sofisticados.
- Gestión compleja en redes grandes con múltiples ACLs.
- Dificultad para detectar tráfico malicioso enmascarado dentro del tráfico permitido.

### **Simple Network Management Protocol (SNMP)**

**SNMP** es un protocolo de administración de redes que permite monitorear y gestionar dispositivos de red como routers, switches y servidores.

**Beneficios:**

- Facilita la administración y supervisión remota de dispositivos.
- Automatiza la detección de fallos y el monitoreo del rendimiento.
- Versiones más seguras (SNMPv3) incluyen autenticación y cifrado.

**Limitaciones:**

- Versiones antiguas (SNMPv1 y SNMPv2) no cifran los datos, lo que puede ser un riesgo de seguridad.
- Vulnerable a ataques de fuerza bruta si no se configura correctamente.

### Syslog Servers

Centraliza los registros de eventos y mensajes de dispositivos y servidores, permitiendo la auditoría y monitoreo de seguridad.

**Beneficios:**

- Centralización de logs para facilitar la supervisión y respuesta ante incidentes.
- Ayuda en la detección de amenazas mediante la correlación de eventos.
- Permite la retención histórica de logs para auditorías.

**Limitaciones:**

- Generación masiva de logs, lo que puede complicar su gestión.
- Si no se asegura adecuadamente, los registros pueden ser vulnerables a manipulación.

### Network Time Protocol (NTP)

Sincroniza los relojes de los dispositivos de red y sistemas con una fuente horaria precisa, esencial para la correcta operación y auditoría de sistemas.

**Beneficios:**

- Sincronización precisa de los eventos de red, fundamental para correlacionar incidentes.
- Mejora la coherencia en logs y auditorías.
- Minimiza problemas relacionados con desfases horarios en sistemas distribuidos.

**Limitaciones:**

- NTP es susceptible a ataques de tipo "Man-in-the-Middle" si no se asegura correctamente (NTPsec o autenticación NTP).

### AAA Servers (Authentication, Authorization, Accounting)

**Descripción**: Los **servidores AAA** (como RADIUS o TACACS+) gestionan la autenticación, autorización y el seguimiento del acceso de usuarios a sistemas y redes.

**Beneficios:**

- Centraliza la autenticación y autorización de usuarios.
- Mejora la seguridad al aplicar políticas de acceso y rastrear la actividad de los usuarios.
- Simplifica la gestión de credenciales en grandes organizaciones.

**Limitaciones:**

- Si el servidor AAA falla, puede bloquear el acceso a toda la red.
- Requiere una configuración cuidadosa para evitar huecos de seguridad.

### Intrusion Detection/Prevention Systems (IDS/IPS)

**Descripción**: Los **IDS** y **IPS** monitorean el tráfico de red para detectar y, en el caso de los IPS, bloquear amenazas como intrusiones o ataques maliciosos.

**Beneficios:**

- Identificación y respuesta ante amenazas en tiempo real.
- Complementa los firewalls al detectar ataques más sofisticados (como exploits o malware).
- IDS permite análisis forense posterior.

**Limitaciones:**

- IDS solo detecta, no previene (a diferencia del IPS).
- Puede generar falsos positivos, lo que dificulta la respuesta efectiva.

### **Virtual Private Network (VPN)**

**Descripción**: **VPN** permite crear conexiones seguras y cifradas sobre redes públicas (como Internet), protegiendo la integridad y confidencialidad de los datos.

**Beneficios:**

- Garantiza la seguridad de las comunicaciones remotas.
- Protege la información sensible al viajar por redes inseguras.
- Cifra los datos, evitando su interceptación.

**Limitaciones:**

- Puede reducir el rendimiento de la red debido al cifrado.
- Vulnerable a ciertos tipos de ataques si no se configura correctamente (por ejemplo, ataques a protocolos antiguos como PPTP).

### **Domain Name System Security Extensions (DNSSEC)**

**Descripción**: **DNSSEC** es una extensión de seguridad para DNS que autentica las respuestas de DNS para evitar ataques de suplantación y envenenamiento de caché.

**Beneficios:**

- Protege contra ataques de suplantación de DNS y envenenamiento de caché.
- Asegura la autenticidad de las respuestas de DNS.

**Limitaciones:**

- No cifra los datos DNS, solo autentica.
- Puede ser complejo de implementar y gestionar en redes grandes.

### **Data Loss Prevention (DLP)**

Es una tecnología que monitorea el tráfico de red y los sistemas para evitar que datos sensibles sean enviados fuera de la red de manera no autorizada.

**Beneficios:**

- Previene fugas de información confidencial (por ejemplo, información personal o datos financieros).
- Ofrece monitoreo continuo del tráfico y del uso de datos.

**Limitaciones:**

- Implementación compleja y puede afectar la productividad si no se configura adecuadamente.
- Puede generar falsos positivos y requiere ajuste constante.