# thz-bench-jvm — Suíte de Benchmarks JMH (Java 25)

Suíte de microbenchmarks de alta performance do THZ-LANG utilizando o framework **JMH (Java Microbenchmark Harness)**. Mede e valida as características de desempenho do motor: aritmética decimal exata sem boxing, alocador contíguo de Arena vs Heap GC e layouts Structure-of-Arrays (SoA) vs Array-of-Structures (AoS).

---

## 📊 Benchmarks Incluídos

| Benchmark | Classe | Descrição |
|---|---|---|
| **Aritmética Decimal** | `DecimalBench` | Operações aritméticas exatas com `DecimalFixo` (soma, multiplicação, divisão e arredondamento half-even) comparadas com baselines |
| **Arena vs GC** | `BlocoMemoriaBench` | Alocação contígua em bloco linear $O(1)$ sem pressão sobre o Garbage Collector vs alocação convencional de objetos em heap |
| **Layout SoA vs AoS** | `LayoutBench` | Eficiência de cache L1/L2 e vetorização comparando Structure-of-Arrays (`LAYOUT_COLUNAR`) com Array-of-Structures tradicional |

---

## 🚀 Como Executar

A partir da raiz do monorepo:
```bash
# Executa todos os benchmarks JMH
./gradlew jmh

# Executa benchmark específico filtrando por nome
./gradlew jmh -Pbenchmark=DecimalBench
```

---

## 📈 Resultados

Os relatórios detalhados com throughput (ops/sec) e latência média são gerados em:
`JVM/thz-bench-jvm/build/results/jmh/results.json`

---

## 📦 Dependência do Core

```kotlin
implementation("thz.lang:thz-core:0.4.0")
```
Resolvido via Gradle Composite Build a partir de `../thz-core-jvm`.
