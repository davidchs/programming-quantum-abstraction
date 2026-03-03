# Programando la abstracción cuántica con registros como unidad de información
## Implementación cuántica de un resolutor SAT mediante PhaseAND y PhaseOR
### Resumen
Este repositorio contiene el código fuente para la implementación en Qiskit de una arquitectura cuántica escalable basada en el algoritmo de Grover, diseñada para resolver problemas de satisfacibilidad booleana (SAT). El enfoque adoptado se fundamenta en la distribución del espacio computacional en múltiples registros independientes, conforme a la metodología de registros paralelos propuesta por (Lin et al., 2023). A través de la evaluación de condiciones en qubits ancilla y la aplicación de operadores lógicos cuánticos de alto nivel, el sistema identifica y amplifica los estados que satisfacen la proposición lógica planteada.

### Fundamentos de la Arquitectura
El modelo desarrollado en este proyecto presenta las siguientes características técnicas:

* **Arquitectura de registros múltiples:** Distribución del procesamiento de las variables lógicas mediante la inicialización de estados entrelazados tipo GHZ. Esto permite la evaluación simultánea y correlacionada de distintas cláusulas de la fórmula.
* **Abstracciones de lógica cuántica:** Diseño modular de operadores booleanos de fase (`PhaseAND`, `PhaseNAND`, `PhaseOR` y `PhaseNOR`). Estos operadores permiten marcar con una fase $\pi$ los estados solución.
* **Diseño de oráculos eficientes:** Integración de oráculos hermíticos para la evaluación de desigualdades y relaciones de equivalencia en aritmética modular (`<`, `>=`, `=`, intervalos). Se emplean las estrategias de optimización para compuertas multicontroladas documentadas por (Sanchez-Rivero et al., 2025).
* **Operador de difusión adaptado:** Implementación de un difusor de Grover específico para esta topología. Dicho operador gestiona rigurosamente el desentrelazamiento, la reflexión espacial sobre la media y el restablecimiento del entrelazamiento.

### Caso de Estudio
El cuaderno computacional principal (`quantum_SAT_solver.ipynb`) demuestra la validez del modelo mediante la resolución empírica de una fórmula lógica expresada en forma normal disyuntiva (DNF). El objetivo es aislar el estado $x$ que satisface la siguiente condición modular:

$$F = [(x > 12) \land (x < 17)] \lor (x = 38) \lor [(x > 39) \land (x < 43)] \lor (x \ge 56) \pmod{64}$$

### Dependencias y Requisitos del Entorno
El modelo ha sido desarrollado en Python. Para la reproducción de los resultados y la correcta ejecución de las simulaciones, se requiere el marco de trabajo Qiskit (versión 2.3). 

Las dependencias pueden ser instaladas mediante el gestor de paquetes de Python:

```bash
pip install qiskit qiskit-aer qiskit-ibm-runtime pylatexenc matplotlib seaborn
```

### Referencias
* Lin, S. W., Wang, T. F., Chen, Y. R., Hou, Z., Sanán, D., & Teo, Y. S. (2023). *A parallel and distributed quantum SAT solver based on entanglement and quantum teleportation*. arXiv preprint arXiv:2308.03344. [https://doi.org/10.48550/arXiv.2308.03344](https://doi.org/10.48550/arXiv.2308.03344)
* Sanchez-Rivero, J., Talaván, D., Garcia-Alonso, J., Ruiz-Cortés, A., & Murillo, J. M. (2025). *Automatic generation of efficient oracles: The less-than case*. Journal of Systems and Software, 219, 112203. [https://doi.org/10.1016/j.jss.2024.112203](https://doi.org/10.1016/j.jss.2024.112203)
