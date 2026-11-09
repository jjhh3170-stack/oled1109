# OLED 실험 7주차 — TADF Exciton Lifetime 측정 및 Rate Constant 계산

**작성자:** 이영빈 **학번:** 2023101942

> 측정 시료: 지연형광(TADF) 재료 **4CzIPN** (toluene, 10<sup>−4</sup> M)<br>
> 측정: RTPL / LTPL 스펙트럼, Time-Resolved PL(TRPL, single photon counting, λ<sub>ex</sub> = 365 nm, λ<sub>em</sub> = 507 nm)

---

## Ⅰ. 실험 목적

- Single photon counting 방식의 Time-Resolved Photoluminescence(TRPL)로 TADF 재료 4CzIPN의 exciton lifetime(τ<sub>p</sub>, τ<sub>d</sub>)을 측정하고 그 의미를 이해한다.
- 측정한 lifetime과 PLQY로부터 들뜬상태의 rate constant(k<sub>p</sub>, k<sub>d</sub>, k<sub>r</sub><sup>S</sup>, k<sub>ISC</sub>, k<sub>RISC</sub>, k<sub>nr</sub><sup>T</sup>)를 계산한다.
- 상온·저온 PL 스펙트럼에서 S<sub>1</sub>과 T<sub>1</sub>을 구하고 ΔE<sub>ST</sub>를 도출하여 TADF가 일어나는 조건을 확인한다.

---

## Ⅱ. 실험 원리

### A. Quantum yield

Quantum yield는 물질이 흡수한 광자 수에 대해 일어난 변화의 수의 비율이다. 광물리 과정에서는 흡수한 광자 수 대비 S<sub>1</sub> 또는 T<sub>1</sub>에서 방출된 형광·인광 광자 수를 뜻한다. 본 실험에서 4CzIPN의 전체 PLQY(Φ<sub>total</sub>)는 94 %이며, 이는 prompt 형광과 delayed 형광의 양자효율 합이다.

> Φ<sub>total</sub> = Φ<sub>p</sub> + Φ<sub>d</sub>

### B. Thermally Activated Delayed Fluorescence (TADF)

일반 형광은 singlet 들뜬상태에서 ns 수준의 수명으로 발광한다. 그런데 일부 재료는 같은 형광 파장에서 μs 수준의 긴 수명을 갖는 발광을 추가로 보이는데, 이를 지연형광이라 한다. 지연형광이 가능한 이유는 ISC로 T<sub>1</sub>에 쌓인 triplet exciton이 **역계간전이(RISC, reverse intersystem crossing)** 로 다시 S<sub>1</sub>이 된 뒤 형광으로 발광하기 때문이다.

보통 S<sub>1</sub>이 T<sub>1</sub>보다 에너지가 높아 S<sub>1</sub> → T<sub>1</sub> 방향의 ISC가 주로 일어난다. 그러나 S<sub>1</sub>과 T<sub>1</sub>의 에너지 차이 ΔE<sub>ST</sub>가 충분히 작으면 상온의 열에너지로 T<sub>1</sub> → S<sub>1</sub> 전이가 일어날 수 있다. 이 과정을 TADF라 하며, 대략 **ΔE<sub>ST</sub> ≲ 0.3 eV**일 때 가능하다고 알려져 있다. 전기 여기 시 생성되는 exciton의 75 %가 triplet이므로, TADF 재료는 이 triplet까지 형광으로 바꿔 이론적으로 내부양자효율 100 %에 가까워질 수 있다.

### C. 들뜬상태의 kinetics

형광 exciton의 수명과 양자효율은 다음과 같다.

> τ<sub>F</sub> = 1 / (k<sub>F</sub> + k<sub>IC</sub> + k<sub>ISC</sub>) = 1 / (k<sub>F</sub> + k<sub>NR</sub>)  ⋯ (1), (2)<br>
> Φ<sub>F</sub> = k<sub>F</sub> / (k<sub>F</sub> + k<sub>IC</sub> + k<sub>ISC</sub>)  ⋯ (3)

TADF 재료의 발광은 수명이 짧은 **prompt 성분(τ<sub>p</sub>)** 과 수명이 긴 **delayed 성분(τ<sub>d</sub>)** 으로 나뉜다. Delayed 성분의 속도상수와 양자효율은 다음 식으로 표현된다.

> 1/τ<sub>d</sub> = k<sub>d</sub> = k<sub>nr</sub><sup>T</sup> + [1 − k<sub>ISC</sub> / (k<sub>r</sub><sup>S</sup> + k<sub>nr</sub><sup>S</sup> + k<sub>ISC</sub>)] · k<sub>RISC</sub>  ⋯ (4)
>
> Φ<sub>d</sub> = Σ (Φ<sub>ISC</sub> · Φ<sub>RISC</sub>)<sup>k</sup> · Φ<sub>p</sub> = [Φ<sub>ISC</sub> · Φ<sub>RISC</sub> / (1 − Φ<sub>ISC</sub> · Φ<sub>RISC</sub>)] · Φ<sub>p</sub>  ⋯ (5)

여기서 k<sub>nr</sub><sup>T</sup>는 T<sub>1</sub>의 비발광 속도상수, k<sub>r</sub><sup>S</sup>와 k<sub>nr</sub><sup>S</sup>는 S<sub>1</sub>의 발광·비발광 속도상수이다. 식 (5)는 exciton이 S<sub>1</sub> ↔ T<sub>1</sub>을 여러 번 오가며 매 순환마다 일부가 형광으로 나간다는 뜻이다. 따라서 지연형광의 세기와 수명은 triplet이 비발광으로 소멸하지 않고 얼마나 많이 RISC 되는지에 따라 결정된다.

### D. TRPL과 IRF

TRPL은 pulse 광원으로 시료를 여기한 뒤, 단일 광자가 검출되기까지의 시간을 반복 측정해 히스토그램으로 쌓는 방식(time-correlated single photon counting)으로 발광 세기의 시간 변화를 얻는다. 측정 곡선에는 광원 pulse 폭과 검출기 응답이 섞여 있으므로, 산란 시료로 장비 응답 함수(IRF, Instrument Response Function)를 따로 측정하고 이를 고려해(deconvolution) fitting 해야 정확한 τ를 얻는다.

### E. S<sub>1</sub>, T<sub>1</sub> 결정

- **S<sub>1</sub>**: 상온 PL(RTPL)은 형광이므로, 스펙트럼의 단파장 쪽 가장자리(onset)에서 S<sub>1</sub> 에너지를 구한다.
- **T<sub>1</sub>**: 저온에서 지연 시간을 두고 측정한 PL(LTPL)은 수명이 긴 인광 성분이 주가 되므로, 그 onset에서 T<sub>1</sub> 에너지를 구한다.

> E [eV] = 1240 / λ<sub>onset</sub> [nm]<br>
> ΔE<sub>ST</sub> = E(S<sub>1</sub>) − E(T<sub>1</sub>)

---

## Ⅲ. 실험 방법

### A. 기구 및 재료

| 구분 | 항목 |
|------|------|
| 측정 장비 | Time-resolved photoluminescence 측정 장비(Hamamatsu, U11487-01 프로그램), PL spectrometer(JASCO) |
| 기구 | 전자저울, 피펫, vial, side arm cell |
| 시료 | 지연형광재료 4CzIPN, 용매 toluene |

### B. 실험 과정

1. 4CzIPN을 toluene에 10<sup>−4</sup> M 농도로 녹인다.
2. U11487-01 프로그램을 실행하고 board select에서 TCC900 모드를 확인한다.
3. 시료를 담은 side arm cell을 TRPL 장비의 샘플 박스에 장착한다.
4. Spectrum measurement에서 여기 파장(장비 고정값 중 가장 가까운 365 nm)과 repetition 10 kHz를 설정해 발광 스펙트럼을 측정한다.
5. Lifetime measurement에서 같은 설정에 emission 파장을 λ<sub>max</sub>(507 nm)로 입력하고 측정한다.
6. IRF measurement로 IRF를 측정한다.
7. 측정 구간과 fitting order를 정해 τ를 도출한다. 측정은 prompt(500 ns 구간), N<sub>2</sub> bubbling 없는 delayed(5 μs 구간), N<sub>2</sub> bubbling 후 delayed(20 μs 구간) 세 가지로 진행했다.

---

## Ⅳ. 실험 결과

### 1. 지연 형광 재료 4CzIPN의 exciton lifetime (τ<sub>p</sub>, τ<sub>d</sub>)을 측정하고 이를 이용하여 k<sub>p</sub>, k<sub>d</sub>, k<sub>r</sub><sup>S</sup>, k<sub>ISC</sub>, k<sub>RISC</sub>, k<sub>nr</sub><sup>T</sup>를 구하시오.

**측정한 lifetime (TRPL fitting 결과)**

| 성분 | 측정 구간 | τ |
|------|-----------|---|
| Prompt fluorescence | 500 ns | **τ<sub>p</sub> = 14.2687 ns** |
| Delayed fluorescence (N<sub>2</sub> bubbling 없음) | 5 μs | τ<sub>d</sub> = 0.0997 μs |
| Delayed fluorescence (N<sub>2</sub> bubbling 진행) | 20 μs | **τ<sub>d</sub> = 2.52191 μs** |

Rate constant 계산에는 산소의 영향을 제거한 τ<sub>p</sub>와 τ<sub>d</sub>(N<sub>2</sub> bubbling)를 사용한다.

**양자효율의 분리.** 전체 PLQY는 Φ<sub>total</sub> = 0.94이다. TCSPC로 측정한 TRPL 곡선의 세기는 단위 시간에 검출된 광자 수이므로, 곡선 아래 면적은 그 구간에 방출된 광자 수에 비례한다. 따라서 N<sub>2</sub> bubbling 후 20 μs 구간 데이터에서 prompt 구간과 delayed 구간의 면적비로 Φ<sub>total</sub>을 나누었다. 두 구간의 경계는 데이터가 τ<sub>d</sub> = 2.52 μs의 delayed 지수 감쇠선에 합류하는 시점(peak 후 80 ns)으로 정했다. 이 시점에서 prompt 성분은 e<sup>−80/14.27</sup> ≈ 0.4 %만 남아 있어 경계 선택에 따른 오차가 작다.

**Fig. 1 — TRPL 면적을 이용한 prompt / delayed 성분 분리 (w/ N<sub>2</sub>, 20 μs 구간)**

![area split](figures/fig_trpl_area.png)

| 구간 | 적분 면적 (counts·ns) | 비율 |
|------|------------------------|------|
| Prompt (0 ~ 80 ns) | 3.21 × 10<sup>5</sup> | 33.7 % |
| Delayed (80 ns 이후) | 6.31 × 10<sup>5</sup> | 66.3 % |

> Φ<sub>p</sub> = 0.94 × 0.337 = 0.317<br>
> Φ<sub>d</sub> = 0.94 × 0.663 = 0.623

**계산 과정.** PLQY가 94 %로 매우 높으므로 S<sub>1</sub>의 비발광 과정은 무시한다(k<sub>nr</sub><sup>S</sup> ≈ 0). 그러면 S<sub>1</sub>에서 빠져나가는 경로는 발광과 ISC 두 가지이다.

> k<sub>p</sub> = 1/τ<sub>p</sub> = 1 / (14.2687 × 10<sup>−9</sup> s) = 7.01 × 10<sup>7</sup> s<sup>−1</sup><br>
> k<sub>d</sub> = 1/τ<sub>d</sub> = 1 / (2.52191 × 10<sup>−6</sup> s) = 3.97 × 10<sup>5</sup> s<sup>−1</sup>
>
> k<sub>r</sub><sup>S</sup> = Φ<sub>p</sub> · k<sub>p</sub> = 0.317 × 7.01 × 10<sup>7</sup> = 2.22 × 10<sup>7</sup> s<sup>−1</sup><br>
> k<sub>ISC</sub> = (1 − Φ<sub>p</sub>) · k<sub>p</sub> = 0.683 × 7.01 × 10<sup>7</sup> = 4.79 × 10<sup>7</sup> s<sup>−1</sup>
>
> k<sub>RISC</sub> = (k<sub>p</sub> · k<sub>d</sub> · Φ<sub>d</sub>) / (k<sub>ISC</sub> · Φ<sub>p</sub>)<br>
> &emsp;&emsp;&ensp;= (7.01 × 10<sup>7</sup> × 3.97 × 10<sup>5</sup> × 0.623) / (4.79 × 10<sup>7</sup> × 0.317) = 1.14 × 10<sup>6</sup> s<sup>−1</sup>
>
> k<sub>nr</sub><sup>T</sup> = k<sub>d</sub> − Φ<sub>p</sub> · k<sub>RISC</sub> = 3.97 × 10<sup>5</sup> − 0.317 × 1.14 × 10<sup>6</sup> = 3.48 × 10<sup>4</sup> s<sup>−1</sup>  (식 (4)에서 1 − Φ<sub>ISC</sub> = Φ<sub>p</sub>)

**검산.** 위 값으로 Φ<sub>ISC</sub> = k<sub>ISC</sub>/k<sub>p</sub> = 0.683, Φ<sub>RISC</sub> = k<sub>RISC</sub>/(k<sub>RISC</sub> + k<sub>nr</sub><sup>T</sup>) = 0.970이다. 이를 식 (5)에 넣으면 Φ<sub>d</sub> = [0.683 × 0.970 / (1 − 0.683 × 0.970)] × 0.317 = 0.623으로, 면적비로 구한 Φ<sub>d</sub>와 일치한다.

**Table 1 — 4CzIPN의 rate constant**

| Rate constant | 값 (s<sup>−1</sup>) | 의미 |
|---------------|-----------|------|
| k<sub>p</sub> | 7.01 × 10<sup>7</sup> | prompt 성분 감쇠 속도 |
| k<sub>d</sub> | 3.97 × 10<sup>5</sup> | delayed 성분 감쇠 속도 |
| k<sub>r</sub><sup>S</sup> | 2.22 × 10<sup>7</sup> | S<sub>1</sub> → S<sub>0</sub> 발광 |
| k<sub>ISC</sub> | 4.79 × 10<sup>7</sup> | S<sub>1</sub> → T<sub>1</sub> 계간전이 |
| k<sub>RISC</sub> | 1.14 × 10<sup>6</sup> | T<sub>1</sub> → S<sub>1</sub> 역계간전이 |
| k<sub>nr</sub><sup>T</sup> | 3.48 × 10<sup>4</sup> | T<sub>1</sub> 비발광 소멸 |

**Fig. 2 — 계산한 rate constant를 표시한 에너지 다이어그램**

![kinetics](figures/fig_kinetics.png)

k<sub>RISC</sub>(1.14 × 10<sup>6</sup> s<sup>−1</sup>)가 k<sub>nr</sub><sup>T</sup>(3.48 × 10<sup>4</sup> s<sup>−1</sup>)보다 약 33배 크다. 즉 T<sub>1</sub>에 모인 exciton의 97 %가 비발광으로 사라지지 않고 다시 S<sub>1</sub>으로 돌아간다(Φ<sub>RISC</sub> = 0.970). k<sub>ISC</sub>가 k<sub>r</sub><sup>S</sup>보다 약 2.2배 커서 S<sub>1</sub> exciton의 68 %가 일단 T<sub>1</sub>으로 넘어가지만, 높은 Φ<sub>RISC</sub> 덕분에 결국 지연형광으로 발광한다. 그 결과 지연형광이 전체 발광의 약 2/3를 차지하고 전체 PLQY가 94 %에 이른다.

**Table 2 — 문헌값(Uoyama et al., 2012)과의 비교**

| 항목 | 실험값 | 문헌값 | 오차율 |
|------|--------|--------|--------|
| τ<sub>p</sub> | 14.27 ns | 17.8 ns | 19.8 % |
| τ<sub>d</sub> | 2.52 μs | 5.1 μs | 50.6 % |
| PLQY | 94 % | 94 % | 0 % |

두 τ가 모두 문헌값보다 짧고, 특히 τ<sub>d</sub>의 차이가 크다. τ<sub>d</sub>는 triplet이 T<sub>1</sub>에 머무는 동안의 소멸 과정에 민감하므로, N<sub>2</sub> bubbling 후에도 용액에 남은 소량의 산소가 triplet을 일부 소광했을 가능성이 가장 크다. 그 밖에 fitting 구간과 order 선택, 용액 농도의 차이도 영향을 주었을 것이다. τ<sub>d</sub>가 짧게 측정되면 k<sub>d</sub>가 커지고, 그만큼 k<sub>RISC</sub>와 k<sub>nr</sub><sup>T</sup>도 함께 커지는 방향으로 계산된다.

### 2. Time resolved PL 그래프를 통해서 지연형광재료 4CzIPN의 발광 현상을 분석하시오.

**Fig. 3 — Prompt 구간(500 ns) TRPL**

![prompt TRPL](figures/fig_trpl_prompt.png)

**Fig. 4 — Delayed 구간 TRPL: (a) N<sub>2</sub> bubbling 전 (5 μs 구간), (b) N<sub>2</sub> bubbling 후 (20 μs 구간)**

![delayed TRPL](figures/fig_trpl_delayed.png)

- **두 가지 감쇠 성분.** Fig. 3에서 발광은 IRF와 함께 즉시 올라간 뒤 τ<sub>p</sub> = 14.27 ns의 단일 지수로 약 50 ns까지 두 자릿수(10<sup>0</sup> → 10<sup>−2</sup>) 감소한다. 그 뒤 곡선이 꺾여 최대값의 약 10<sup>−2</sup> 수준에서 매우 천천히 줄어드는 꼬리가 이어진다. 이 꼬리가 μs 수명의 delayed 성분이다. 같은 파장(507 nm)에서 ns와 μs 두 성분이 함께 관측된다는 것은, 같은 S<sub>1</sub>에서 나오는 형광이 두 경로로 만들어진다는 뜻이다.
- **Prompt 성분.** 광여기로 직접 생성된 S<sub>1</sub> exciton이 바로 발광(k<sub>r</sub><sup>S</sup>)하거나 ISC로 T<sub>1</sub>이 되며 사라지는 과정이다. 수명은 k<sub>p</sub> = k<sub>r</sub><sup>S</sup> + k<sub>ISC</sub>로 정해진다.
- **Delayed 성분.** Fig. 4(b)의 N<sub>2</sub> bubbling 데이터에서 delayed 성분은 약 15 μs 동안 세 자릿수 이상 단일 지수(τ<sub>d</sub> = 2.52 μs)로 감소한다. τ<sub>d</sub>가 τ<sub>p</sub>보다 약 180배 길다. T<sub>1</sub>으로 넘어간 exciton이 RISC로 S<sub>1</sub>에 돌아와 발광하는 과정이 반복되므로, 발광 파장은 형광과 같지만 수명은 triplet이 S<sub>1</sub>으로 돌아오는 속도에 의해 결정된다.
- **산소의 영향.** N<sub>2</sub> bubbling을 하지 않은 시료(Fig. 4(a))는 delayed 성분의 수명이 0.10 μs로 약 25배 짧아지고 세기도 빠르게 사라진다. 반면 prompt 성분은 큰 변화가 없다. 산소가 triplet exciton을 선택적으로 소광한다는 뜻이며, 이는 delayed 성분이 triplet을 거쳐 나오는 TADF임을 보여주는 직접적인 증거이다.

정리하면 4CzIPN의 발광은 ns 수명의 prompt 형광과 RISC를 거친 μs 수명의 지연형광으로 이루어지며, 지연형광이 산소에 민감하다는 점에서 TADF 재료임을 확인할 수 있다.

### 3. 지연형광 재료 4CzIPN의 PL 스펙트럼을 통해서 S<sub>1</sub>과 T<sub>1</sub>을 각각 구하고 ΔE<sub>ST</sub>를 도출하시오.

**Fig. 5 — 4CzIPN의 RTPL / LTPL 스펙트럼과 onset 작도**

![RT LT PL](figures/fig_rt_lt_pl.png)

각 스펙트럼의 단파장 쪽 상승부에서 기울기가 가장 큰 지점에 접선을 긋고, 접선이 x축(세기 0)과 만나는 파장을 onset으로 정했다.

| 스펙트럼 | λ<sub>max</sub> | λ<sub>onset</sub> | 에너지 |
|----------|------|--------|--------|
| RTPL (형광) | 509.0 nm | 456.3 nm | **S<sub>1</sub> = 1240 / 456.3 = 2.72 eV** |
| LTPL (인광, 30 ms delay) | 503.5 nm | 460.8 nm | **T<sub>1</sub> = 1240 / 460.8 = 2.69 eV** |

> ΔE<sub>ST</sub> = S<sub>1</sub> − T<sub>1</sub> = 2.718 − 2.691 = 0.027 eV (27 meV)

ΔE<sub>ST</sub>는 TADF가 가능한 기준(약 0.3 eV)보다 훨씬 작고, 상온 열에너지 k<sub>B</sub>T(약 26 meV)와 비슷하다. 그래서 T<sub>1</sub>의 exciton이 상온에서 쉽게 S<sub>1</sub>으로 올라갈 수 있으며, 결과 1에서 k<sub>RISC</sub>가 k<sub>nr</sub><sup>T</sup>보다 약 33배 크게 나온 것과도 맞는다.

**Table 3 — 문헌값과의 비교**

| 항목 | 실험값 | 문헌값 (Uoyama et al., 2012) | 오차율 |
|------|--------|------------------------------|--------|
| ΔE<sub>ST</sub> | 0.027 eV | 0.083 eV | 67.5 % |

ΔE<sub>ST</sub>가 문헌값보다 작게 나온 이유로는 다음을 생각할 수 있다.

- LTPL은 저온에서 측정하므로 용매가 얼어 분자 주변 환경과 CT 상태의 안정화 정도가 상온과 다르다. 그래서 두 스펙트럼의 onset을 직접 비교하면 ΔE<sub>ST</sub>가 실제와 달라질 수 있다.
- Onset 값은 접선을 긋는 위치에 민감하다. 두 스펙트럼의 onset 차이가 4.5 nm에 불과해, 1~2 nm의 판독 차이도 ΔE<sub>ST</sub>를 수십 % 바꾼다.

### 4. Solution TRPL에서 N<sub>2</sub> Bubbling 과정을 해주어야 하는 이유를 설명하시오.

산소 분자(O<sub>2</sub>)는 바닥상태가 triplet(<sup>3</sup>Σ<sub>g</sub><sup>−</sup>)인 특이한 분자이다. 용액에 녹아 있는 산소가 들뜬 분자와 충돌하면, triplet exciton의 에너지를 받아 singlet oxygen(<sup>1</sup>O<sub>2</sub>)이 되면서 exciton을 비발광으로 소멸시킨다(triplet–triplet energy transfer). 4CzIPN의 T<sub>1</sub>은 2.69 eV로 singlet oxygen 생성에 필요한 에너지(약 0.98 eV)보다 훨씬 높아 이 소광이 효율적으로 일어난다.

TADF의 delayed 성분은 T<sub>1</sub>에 머무는 동안(μs) RISC를 기다려야 하므로, 이 긴 시간 동안 산소와 충돌할 확률이 높다. 따라서 산소가 남아 있으면 triplet이 RISC 대신 산소에 의해 소멸하고, 지연형광의 수명과 세기가 실제보다 크게 줄어든다. 본 실험에서도 N<sub>2</sub> bubbling 전 τ<sub>d</sub>는 0.10 μs였지만 bubbling 후에는 2.52 μs로 약 25배 길어졌다. 원 논문에서도 산소 포화 시 PLQY가 94 %에서 10 %로 떨어졌다.

N<sub>2</sub> bubbling은 용액 속 산소를 불활성 기체로 밀어내 이 소광 경로를 없애는 과정이다. 이렇게 해야 측정한 τ<sub>d</sub>와 PLQY가 재료 고유의 RISC와 triplet 소멸 특성을 반영하며, 이를 바탕으로 계산한 k<sub>RISC</sub>, k<sub>nr</sub><sup>T</sup>도 의미를 갖는다.

### 5. 4CzIPN과 같은 D-A타입의 TADF물질의 ΔE<sub>ST</sub>를 줄이기 위한 방법을 설명하시오.

S<sub>1</sub>과 T<sub>1</sub>은 같은 HOMO → LUMO 전이에서 생기지만, 전자 스핀 배열에 따른 교환 에너지(exchange energy) 때문에 에너지가 갈린다. 교환 적분을 J라 하면 대략 다음과 같다.

> E(S<sub>1</sub>) ≈ E<sub>0</sub> + J,  E(T<sub>1</sub>) ≈ E<sub>0</sub> − J  →  ΔE<sub>ST</sub> ≈ 2J

J는 HOMO와 LUMO 파동함수가 공간적으로 겹치는 정도에 비례한다. 따라서 **HOMO와 LUMO를 분자 안에서 공간적으로 분리**하면 ΔE<sub>ST</sub>를 줄일 수 있다. D-A 타입 분자에서는 다음 방법을 쓴다.

- **Donor와 acceptor에 HOMO와 LUMO를 나누어 배치한다.** 전자가 풍부한 donor(4CzIPN에서는 carbazole)에 HOMO가, 전자가 부족한 acceptor(dicyanobenzene)에 LUMO가 놓이도록 설계한다. 이때 들뜬상태는 D → A 분자 내 전하이동(ICT) 성격을 갖는다.
- **D–A 사이를 크게 비틀어 연결한다.** Donor와 acceptor가 같은 평면에 있으면 π 궤도가 이어져 HOMO와 LUMO가 겹친다. 부피가 큰 치환기의 입체 장애로 D–A 결합의 비틀림 각(dihedral angle)을 키우면 π 공액이 끊겨 겹침이 줄어든다. 4CzIPN은 4개의 carbazole이 dicyanobenzene 둘레에 빽빽하게 붙어 있어 서로 밀어내며 크게 비틀어진 구조를 만든다.
- **강한 donor와 강한 acceptor를 조합한다.** 전자 주개·받개 능력이 클수록 HOMO는 donor에, LUMO는 acceptor에 더 국재화되어 겹침이 줄어든다.
- **Donor를 여러 개 붙인다.** 4CzIPN처럼 donor를 여러 개 배치하면 HOMO가 donor들에 퍼지고 acceptor 중심의 LUMO와 더 확실히 분리된다.

다만 HOMO–LUMO 겹침이 0에 가까워지면 S<sub>1</sub> → S<sub>0</sub> 전이의 진동자 세기도 작아져 k<sub>r</sub><sup>S</sup>가 감소한다. 따라서 실제 설계에서는 ΔE<sub>ST</sub>를 충분히 작게 하면서도 k<sub>r</sub><sup>S</sup>가 유지될 만큼의 겹침을 남기는 균형이 필요하다. 4CzIPN은 carbazole의 비틀림이 완전한 직교가 아니어서 겹침이 약간 남아 있으며, 작은 ΔE<sub>ST</sub>와 높은 PLQY를 함께 얻을 수 있다.

---

### 참고문헌

1. H. Uoyama, K. Goushi, K. Shizu, H. Nomura, C. Adachi, *Nature* **492**, 234–240 (2012).
2. Q. Zhang, B. Li, S. Huang, H. Nomura, H. Tanaka, C. Adachi, *Nature Photonics* **8**, 326–332 (2014).

### 부록 — 데이터 처리 요약

- PL: `4CzIPN_RTPL.csv`, `4CzIPN_LTPL 30ms.csv` (JASCO). 최대값으로 정규화한 뒤 단파장 상승부의 최대 기울기 지점(±4 nm)에서 선형회귀로 접선을 구하고 x절편을 onset으로 사용하였다.
- TRPL: `.dat`(시료)와 `.irf`(IRF) 파일. 각 곡선은 peak 이전 구간 평균으로 배경을 빼고 최대값으로 정규화하여 로그 축에 그렸다. τ는 조교가 장비에서 fitting하여 제공한 값을 사용하였다.
- Φ<sub>p</sub>, Φ<sub>d</sub>: N<sub>2</sub> bubbling 후 20 μs 구간 TRPL을 배경 보정한 뒤, peak 직전부터 80 ns까지(prompt)와 그 이후(delayed)의 면적을 직접 적분하여 면적비로 Φ<sub>total</sub> = 0.94를 나누었다.
- 모든 그래프는 측정 raw data로부터 Python(numpy/matplotlib)으로 직접 작성하였다.
