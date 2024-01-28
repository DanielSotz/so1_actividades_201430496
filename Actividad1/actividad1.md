# Actvidad 1

## 1. Tipos de Kernel y sus diferencias

* Kernel Monolítico: es un tipo de núcleo de sistema operativo que integra todas las funciones esenciales directamente en el núcleo central del sistema. Todas las rutinas del sistema operativo, como la gestión de memoria, la administración de procesos y los controladores de dispositivos, residen en el mismo espacio de memoria.
    
* Kernel Microkernel: adopta un enfoque más modular. Solo las funciones esenciales, como la gestión de memoria y la programación de procesos, residen en el núcleo central. Otras funciones, como controladores de dispositivos y sistemas de archivos, se ejecutan como procesos independientes fuera del núcleo central.

|Característica | Kernel Monolítico | Kernel Microkernel    |
| ------------- | ----------------- | -------------------   |
| Estructura principal  | Un solo bloque grande con todas las funciones   | Estructura dividida, con funciones básicas en el núcleo central y otras en módulos externos. |
| Ventajas  | - Puede ser eficiente para tareas específicas. | - Mayor flexibilidad y modularidad. |
| | - Menos sobrecarga en la comunicación interna. | - Facilita la actualización y mantenimiento de componentes. |
| Desventajas | - Puede ser menos flexible y más difícil de mantener | - Puede tener un rendimiento ligeramente inferior en algunas tareas intensivas debido a la comunicación entre módulos.|
| Ejemplo de sistema | Linux, Windows (en gran medida), macOS. | QNX, MINIX.


## 2. User vs Kernel Mode

|Característica | User Mode | Kernel Mode   |
| ------------- | ----------------- | -------------------   |
| Definición | Entorno en el que se ejecutan las aplicaciones y procesos no privilegiados en un sistema operativo. Este modo garantiza que las aplicaciones de usuario no puedan realizar acciones que comprometan la estabilidad del sistema.    | Entorno privilegiado donde se ejecuta el núcleo del sistema operativo. Este modo es esencial para realizar operaciones críticas y proporcionar servicios fundamentales para el funcionamiento del sistema operativo. |
|Funciones permitidas | Se ejecutan funciones no privilegiadas. Las aplicaciones de usuario no tienen el privilegio de realizar operaciones que puedan afectar directamente al sistema operativo o a otros procesos. Las funciones permitidas son aquellas destinadas a la interacción con el usuario y la realización de tareas específicas de la aplicación.|Tiene la capacidad de ejecutar todas las funciones del sistema, desde la gestión de procesos y memoria hasta la manipulación directa del hardware. Este modo permite al núcleo realizar operaciones de bajo nivel, como el manejo de interrupciones y la gestión eficiente de recursos, lo que es esencial para el funcionamiento y la estabilidad del sistema operativo.|
|Acceso a recursos |Las aplicaciones de usuario tienen acceso limitado a los recursos del sistema. Este acceso se concede de acuerdo con las políticas de seguridad y los permisos asignados. Las aplicaciones de usuario dependen del Kernel Mode para acceder a recursos de bajo nivel y realizar operaciones críticas. | El núcleo del sistema operativo tiene acceso completo a todos los recursos del sistema, incluyendo la gestión directa de hardware y memoria. Este modo permite al núcleo realizar operaciones críticas sin restricciones y garantiza el control total sobre los componentes del sistema|
|Cambios en el hardware | No puede realizar cambios directos en el hardware y depende del núcleo para acceder a recursos de bajo nivel. | Puede realizar cambios directos en el hardware y acceder a recursos de bajo nivel.| 
Manejo de interrupciones | No puede manejar interrupciones directamente. Debe pasar al Kernel Mode para que el núcleo las maneje. | Puede manejar interrupciones directamente sin tener que cambiar de modo.
Seguridad |  Proporciona un mayor nivel de seguridad, pues las aplicaciones de usuario están aisladas y no pueden afectar directamente al sistema operativo o a otros procesos. Las restricciones de acceso limitan las posibles amenazas que pueden surgir desde el espacio de usuario.  | Al tener acceso total a los recursos del sistema, implica un menor nivel de seguridad.  La seguridad en este modo es crítica para evitar vulnerabilidades y asegurar el buen funcionamiento del sistema.

## 3. Interruptions vs Traps

|Característica | Interrupts | Traps    |
| ------------- | ----------------- | -------------------   |
| Definición | Señales externas al procesador que provienen de dispositivos o eventos externos. Estas interrumpen la ejecución normal y requieren que el sistema operativo atienda la solicitud. | Eventos o condiciones generadas internamente durante la ejecución de un programa, como solicitar servicios del sistema operativo.
Prioridad | Tienen niveles de prioridad y pueden ser enmascaradas o deshabilitadas temporalmente para gestionar la concurrencia. | Generalmente no tienen niveles de prioridad y son generadas por el propio programa, por lo que están vinculadas directamente a su ejecución.
Fuente | Proviene de eventos externos, como señales de hardware que requieren atención del sistema operativo. | Generadas internamente durante la ejecución de un programa debido a condiciones específicas, como intentos de ejecutar instrucciones privilegiadas.
Control de flujo | Pueden cambiar el flujo de ejecución del programa actual hacia un controlador de interrupciones. |  Pueden cambiar el flujo de ejecución, pero a menudo se utilizan para manejo de errores u operaciones específicas en el mismo contexto del programa actual.
Ejemplo | Interrupción de temporizador que ocurre a intervalos regulares para permitir al sistema operativo realizar tareas de planificación. | Trampa de división por cero generada cuando un programa intenta dividir entre cero.