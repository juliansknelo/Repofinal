# **Antecedentes**

La transición estratégica hacia un modelo de inteligencia de negocio basado en Data Lake constituye un cambio de paradigma fundamental para superar las limitaciones estructurales de la infraestructura tradicional, permitiendo alcanzar una agilidad empresarial extrema y una escalabilidad horizontal ilimitada. Esta arquitectura avanzada optimiza el Costo Total de Propiedad (TCO) al mitigar el gasto en licenciamiento propietario y hardware especializado, garantizando simultáneamente la integridad absoluta de los activos de información mediante una gestión de datos inmutable y centralizada. La implementación aborda y resuelve de manera directa los problemas críticos de fragmentación operativa y riesgo sistémico derivados de una visión empresarial descoordinada, eliminando la dependencia de volcados manuales por parte de administradores de bases de datos y la proliferación de silos tecnológicos en hojas de cálculo aisladas. A través de la unificación de los sistemas transaccionales y analíticos, se mitigan las roturas de stock recurrentes en modelos de negocio de proximidad y se supera la incapacidad previa para realizar análisis geográficos y de segmentación local que anteriormente limitaban el impacto de las campañas estratégicas. El despliegue de esta solución se fundamenta en métricas de alto rendimiento diseñadas para soportar la operación de 1,050 tiendas —incluyendo las 250 aperturas proyectadas— y procesar un volumen masivo de 415 millones de transacciones anuales. Asimismo, la arquitectura permite la ingesta y el análisis del comportamiento de 1.300 millones de visitantes anuales provenientes de logs de servidores web, transformando datos brutos en una base de realidad única que asegura una precisión financiera del 100%. Este enfoque técnico integral permite la democratización del dato y el soporte de decisiones en tiempo cuasi-real, estableciendo el cimiento necesario para que la organización evolucione hacia un modelo dirigido por datos capaz de dominar el competitivo sector del retail moderno.  
El Business Intelligence (BI) ha transitado de ser una solución de nicho, confinada a informes estáticos y silos tecnológicos, a convertirse en un ecosistema abierto de Big Data que actúa como el sistema nervioso central de las organizaciones modernas. Históricamente, el BI dependía de arquitecturas propietarias cerradas que forzaban ciclos rígidos de procesamiento por lotes, limitando la capacidad de maniobra ante cambios súbitos en el mercado. Hoy, la competitividad se define por la agilidad en el procesamiento de volúmenes masivos de información, donde la capacidad de transformar datos brutos en decisiones ejecutivas en cuestión de minutos marca la diferencia entre el liderazgo sectorial y la obsolescencia operativa.  
Técnicamente, esta evolución se sintetiza en el paso de sistemas monolíticos y costosos —liderados por proveedores tradicionales como Oracle o IBM— hacia plataformas basadas en Apache Hadoop bajo estándares de código abierto. Mientras que las soluciones propietarias imponían procesos de carga restrictivos y licencias por volumen que asfixiaban el crecimiento, las distribuciones modernas como Hortonworks (HDP) o Cloudera ofrecen una escalabilidad horizontal sin precedentes. Este modelo permite pasar de procesos de extracción lentos hacia un paradigma donde los datos fluyen en tiempo "cuasi-real" hacia un núcleo de almacenamiento unificado. Sin embargo, la tecnología por sí sola no es el fin; su valor real reside en su capacidad para resolver desafíos logísticos y estratégicos críticos, como los que actualmente enfrenta Supermercados Sierra en su agresivo plan de expansión.

## **Del Data Warehouse al Data Lake**

La transición del Data Warehouse (DW) tradicional al Data Lake no es solo una actualización de software, sino un cambio de paradigma hacia la agilidad empresarial extrema. Mientras el DW exige que el dato se adapte a un molde predefinido antes de guardarse, el Data Lake permite que la empresa respire con sus datos en formato nativo, postergando la estructura hasta el momento preciso del consumo.  
Diferenciación Estratégica  
La siguiente tabla detalla por qué el modelo tradicional es insuficiente para la escala de Supermercados Sierra:  
Característica  
Data Warehouse Tradicional  
Data Lake (Apache Hive)  
Paradigma  
Schema-on-Write (Rígido)  
Schema-on-Read (Flexible)  
Ingesta de Datos  
Lenta (requiere transformación previa)  
Inmediata (carga inmediata en formato nativo)  
Gobernanza/Latencia  
Alta latencia de actualización  
Baja latencia; acceso inmediato a eventos  
Escalabilidad  
Vertical y costosa (Vendor Lock-in)  
Horizontal e ilimitada (Nodos dinámicos)  
Costo Total (TCO)  
Elevado (Licenciamiento por TB)  
Optimizado (Código abierto y hardware commodity)  
Evaluación de la Flexibilidad  
El Data Lake implementa un almacenamiento "append-only", asegurando la inmutabilidad de los registros históricos. Mediante el uso de Apache Hive, podemos aplicar esquemas retroactivos a los 415 millones de transacciones anuales estimadas. Optimizamos la recuperación según el caso de uso: utilizamos el formato AVRO para operaciones que requieren filas completas (ideal para procesos de preparación de pedidos) y el formato ORC (columnar) para consultas analíticas masivas que filtran subconjuntos de datos, reduciendo drásticamente los tiempos de respuesta.

## **4\. Optimización de Procesos: Ciclo ELT y Datos en Tiempo Real**

Para garantizar la integridad de los reportes financieros y la eficiencia operativa, Supermercados Sierra debe migrar del ciclo ETL (Extraer-Transformar-Cargar) hacia un modelo ELT (Extraer-Cargar-Transformar). Al utilizar tablas externas de Hive, los datos están disponibles inmediatamente después de la carga, eliminando los cuellos de botella del procesamiento previo.  
Transformación del Proceso de Ingesta  
Implementamos la solución sobre Hortonworks HDP versión 2.6.5.0 ejecutándose en Ubuntu Server 14.04 LTS, utilizando herramientas líderes del ecosistema:  
Apache Sqoop: Automatiza la carga masiva desde el sistema de TPV (MySQL) hacia Hive, permitiendo actualizaciones incrementales de los tickets de venta.  
Apache Flume: Captura y unifica los logs de los servidores web de forma distribuida, eliminando puntos únicos de fallo en la captura del tráfico online.  
Apache Kafka: Gestiona el flujo de eventos de e-commerce en tiempo real, permitiendo que las ventas online se procesen como un stream continuo.  
Arquitectura Lambda  
Para resolver el problema crónico de falta de stock, implementamos una Arquitectura Lambda. La Capa de Lote (Batch Layer) procesa los 415 millones de transacciones anuales para identificar tendencias de consumo a largo plazo. Simultáneamente, la Capa de Velocidad (Speed Layer) mediante Kafka procesa los pedidos del momento, permitiendo que la operativa en tienda reserve productos para los repartidores de forma inmediata (ventana de 30 min). Este equilibrio es lo que transforma la infraestructura en una ventaja competitiva real.

## **Visualización de Reportes Financieros**

Estructura de Reportes Estratégicos  
El diseño de visualización se desglosa en beneficios tangibles:  
Cuadro de Mando Ejecutivo: Visión 360° de la salud financiera de la cadena, integrando ventas físicas y digitales para evaluar el ROI de las 250 nuevas aperturas.  
Gestión de Ventas y Finanzas: Operativa en Tiempo Real: Gestión de stock JIT para pedidos e-commerce. Permite a los encargados de tienda (\<150m²) visualizar la demanda entrante y optimizar la ruta de los repartidores externos.  
Soporte Tecnológico de Alto Rendimiento  
Para consultas SQL complejas sin latencia, integramos Apache Kylin, que pre-computa cubos OLAP utilizando HBase como almacenamiento intermedio. Aunque Kylin requiere una instalación manual al no formar parte del stack base de HDP, su capacidad para ejecutar consultas sobre miles de millones de filas en segundos es vital. Complementamos esto con Apache Superset para una exploración interactiva y granular de los datos financieros.

## **6\. Conclusiones y Valor Proyectado**

La implementación de un Data Lake bajo el paradigma de Hortonworks HDP no es solo una mejora técnica; es la base de una ventaja competitiva sostenible para Supermercados Sierra. Al unificar el BI tradicional con el análisis predictivo, la compañía deja de ser reactiva para convertirse en una organización dirigida por datos (data-driven).  
Sintetización de Beneficios  
Escalabilidad Virtualmente Ilimitada: Capacidad para integrar datos de 1,050 tiendas (800 actuales \+ 250 previstas) sin degradación de rendimiento.  
Reducción de Duplicidad: Eliminación de silos entre el análisis de Big Data y el Data Warehouse tradicional en un único ecosistema.  
Soporte Predictivo Avanzado: Base para modelos de "Análisis de Cesta de la Compra" que incrementan el ticket medio mediante recomendaciones personalizadas.  
Democratización del Dato: Uso de herramientas Open Source que eliminan el Vendor Lock-in de proveedores como Oracle o IBM.  
Impacto Financiero y TCO  
Desde una perspectiva financiera, esta arquitectura optimiza drásticamente el Costo Total de Propiedad (TCO). Al evitar licencias propietarias por volumen en un escenario de crecimiento exponencial de datos, Supermercados Sierra puede reinvertir esos ahorros en su red logística. La unificación de plataformas garantiza que la dirección reciba reportes financieros con una precisión del 100%, eliminando las discrepancias de los volcados manuales y proporcionando la agilidad necesaria para dominar el sector retail de proximidad.

# **Marco Teórico de la Ingeniería de Datos y Gestión Empresarial**

## ---

**1\. Modelado Dimensional: La Fundación de la Analítica**

El modelado dimensional, conceptualizado principalmente por Ralph Kimball y Margy Ross en su obra fundamental *"The Data Warehouse Toolkit"*, se establece como la técnica de diseño de bases de datos de referencia para sistemas de soporte a la decisión. A diferencia del modelado de entidad-relación (ER) utilizado en sistemas transaccionales (OLTP), el cual busca eliminar la redundancia mediante la normalización, el modelado dimensional prioriza la legibilidad y el rendimiento de las consultas analíticas (OLAP).

### **1.1. El Proceso de Diseño de Cuatro Pasos**

Kimball propone una metodología rigurosa para la construcción de modelos dimensionales:

1. **Selección del proceso de negocio:** Se identifica el evento operativo que genera datos (ej. una transacción de venta, un registro de sensor).  
2. **Declaración del grano:** Es el paso más crítico; define qué representa exactamente una fila en la tabla de hechos. Un grano fino (atómico) permite mayor flexibilidad que uno agregado.  
3. **Identificación de las dimensiones:** Representan el contexto del evento ("quién", "qué", "dónde", "cuándo").  
4. **Identificación de los hechos:** Son las métricas cuantitativas que resultan del proceso de negocio.

### **1.2. Estructuras del Esquema**

El modelo resultante suele adoptar la forma de un **Esquema de Estrella**, donde una tabla de hechos central está rodeada por tablas de dimensiones desnormalizadas. El **Esquema de Copo de Nieve** es una variación donde las dimensiones se normalizan parcialmente, aunque suele evitarse en entornos analíticos puros por la complejidad que añade a las consultas SQL.

| Componente | Características Técnicas | Función Analítica |
| :---- | :---- | :---- |
| **Tablas de Hechos** | Contienen claves foráneas (FK) y medidas numéricas. | Soportar agregaciones (SUM, AVG) y cálculos de KPI. |
| **Tablas de Dimensiones** | Contienen atributos descriptivos (texto) y claves subrogadas. | Proporcionar filtros, agrupaciones y etiquetas para reportes. |

## 

## **2\. De Data Warehouse a Data Lakehouse: Un Cambio de Paradigma**

La arquitectura de datos ha evolucionado significativamente, pasando del **Data Warehouse (DW)** tradicional, que era rígido ante datos no estructurados y caro de escalar, al **Data Lake**, que ofrecía almacenamiento masivo y económico, pero que a menudo se degradaba en un "pantano de datos" por su falta de esquemas y transaccionalidad. El **Data Lakehouse** surgió para resolver estas deficiencias, combinando las funciones de gestión y rendimiento del DW e implementándolas directamente sobre el almacenamiento de objetos del Data Lake. Según Armbrust et al. (2021) en *"Lakehouse: A New Generation of Open Platforms..."*, los pilares fundamentales de esta arquitectura incluyen: la provisión de **Transacciones ACID** para garantizar la integridad de los datos en escrituras concurrentes, la capacidad de manejar **Esquemas Evolutivos** sin interrupción del servicio, y el **Soporte Nativo para IA y ML** al permitir el acceso directo a los archivos para algoritmos de ciencia de datos sin capas SQL intermedias.

## **3\. Arquitectura Medallion: Calidad de Datos por Capas**

En el contexto de los Data Lakehouses modernos, la arquitectura Medallion (o arquitectura de capas de calidad) proporciona un flujo lógico para el refinamiento de la información. Piethein Strengholt describe este enfoque como un método para gestionar la "fuente de verdad" de manera incremental.

### **3.1. Capa Bronze (Raw)**

Es el punto de entrada. Los datos se almacenan en su estado nativo, tal como provienen de la fuente (ERP, APIs, IoT). No se aplican transformaciones, permitiendo que esta capa actúe como un registro histórico inmutable para futuras re-procesos.

### **3.2. Capa Silver (Trusted)**

En esta etapa, se aplican procesos de limpieza, filtrado y normalización básica. Los datos se transforman a formatos optimizados (como Parquet o Delta). Es la capa donde se resuelven las inconsistencias de tipos de datos y se aplican reglas de validación iniciales.

### **3.3. Capa Gold (Curated)**

Representa el nivel más alto de refinamiento. Aquí los datos se organizan siguiendo modelos dimensionales (Kimball) o estructuras agregadas específicas para casos de uso de negocio, como cuadros de mando integrales o modelos de aprendizaje automático.

## 

## **4\. Ingeniería de Pipelines y Orquestación con Apache Airflow**

Un **Pipeline de Datos** constituye la infraestructura esencial para mover información desde un sistema de origen hacia un destino, aplicando transformaciones críticas en el proceso. Dada la creciente complejidad de estos flujos, la orquestación se vuelve indispensable. Apache Airflow, siguiendo la filosofía "Workflow as Code" (basada en la obra de Harenslak y de Ruiter), aborda esta necesidad al permitir la definición de flujos de trabajo mediante código Python, lo que facilita el uso de control de versiones, pruebas unitarias y la colaboración entre ingenieros. La representación lógica de este pipeline se materializa en un **Grafo Acíclico Dirigido (DAG)**, cuyas propiedades son fundamentales: debe ser **Dirigido** para establecer un orden claro de ejecución de las tareas, **Acíclico** para asegurar que el flujo avance siempre hacia un final sin bucles infinitos, y su ejecución debe ser **Idempotente**, lo que garantiza que los mismos parámetros produzcan siempre el mismo resultado, facilitando así la recuperación ante fallos.

## **5\. Tecnologías de Procesamiento Analítico: DuckDB**

DuckDB representa una innovación en el ámbito de las bases de datos analíticas embebidas. Needham y Hunger destacan su capacidad para realizar procesamiento OLAP directamente en el entorno de ejecución del usuario (in-process), eliminando la latencia de red de los sistemas cliente-servidor tradicionales. Además, a diferencia de los motores de bases de datos tradicionales que procesan una fila a la vez, DuckDB utiliza ejecución vectorizada, procesando grandes bloques de datos simultáneamente. Esta técnica optimiza el uso de la caché de la CPU y permite un rendimiento superior en consultas complejas sobre grandes volúmenes de datos.

## **6\. Pipelines Declarativos y el Rol de SQLMesh**

La ingeniería de datos está experimentando una transición de pipelines imperativos, donde cada paso debe programarse explícitamente, hacia **pipelines declarativos**, en los cuales el ingeniero describe el estado final deseado de los datos y el sistema subyacente gestiona su ejecución óptima. En este contexto, SQLMesh emerge como una solución fundamental que integra conceptos avanzados de desarrollo de software para la gestión del ciclo de vida de los datos. Sus funcionalidades clave incluyen los **Virtual Data Environments**, que facilitan la creación de entornos aislados para pruebas sin la duplicación física de datos; la **Planificación Automática**, que identifica inteligentemente qué modelos deben ser recalculados tras cambios en el código para optimizar los costos computacionales; y una **Auditoría Integrada**, que permite el seguimiento detallado de las modificaciones en la estructura de los datos.

## 

## **7\. Gobierno de Datos: Marco Estratégico**

El gobierno de datos (Data Governance) se define, según John Ladley, como el ejercicio de la toma de decisiones y la autoridad sobre los activos de datos; sus componentes clave incluyen las Políticas y Estándares (reglas sobre cómo se definen y utilizan los datos), el Data Stewardship (roles responsables de la calidad y el significado de los datos en áreas de negocio específicas) y el Catálogo de Datos (herramienta técnica que documenta el linaje, la definición y el uso de los datos en la organización). Además, la gobernanza se apoya en roles fundamentales como el **Data Owner (Dueño de los Datos)**, que tiene la máxima responsabilidad sobre la calidad, seguridad y cumplimiento normativo de un activo específico; el **Data Producer (Productor de Datos)**, que genera o introduce datos en el ecosistema; el **Data Consumer (Consumidor de Datos)**, que accede y utiliza los datos para análisis y soporte de procesos; el **Data Custodian (Custodio de Datos)**, que se encarga de la gestión técnica, almacenamiento y seguridad operativa; y el **Data Governance Manager (Gerente de Gobierno de Datos)**, quien lidera y coordina las actividades del programa para asegurar la aplicación de políticas y estándares.

## 

## **8\. Sistemas ERP y el Ecosistema Odoo**

Los sistemas de **Planificación de Recursos Empresariales (ERP)** actúan como la columna vertebral operativa de una organización, integrando procesos que anteriormente residían en silos aislados. Odoo, como se detalla en *"Working with Odoo"* de Greg Moss, destaca por su arquitectura modular basada en una pila tecnológica moderna (Python y PostgreSQL), lo que permite una integración perfecta entre módulos clave como Fabricación (MRP) para el control de órdenes de producción, Gestión de Inventarios con seguimiento en tiempo real, y Finanzas y Contabilidad para la automatización de asientos. En el ecosistema moderno, el ERP es la fuente de datos más crítica para el análisis de negocio, y el modelado dimensional debe ser capaz de extraer datos de sus tablas normalizadas (como las de Odoo) para transformarlos en estructuras de estrella que faciliten la visibilidad ejecutiva sobre la cadena de suministro y la rentabilidad.

## ---

