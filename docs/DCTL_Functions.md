# Fusion Fuse用 DCTL関数リファレンス

このドキュメントは、Fusion Fuse内で使用可能なDCTL（DaVinci Color Transform Language）関数の包括的なリストを提供します。内容は **Fusion 18 Fuse SDK Manual**（p.132–134）に基づいています。これらの関数は、CUDA、OpenCL、Metalといった異なるGPUエンジン間での互換性を保つように設計されています。

> [!IMPORTANT]
> - すべての `float` リテラルには **必ず** `f` 接尾辞を付けてください（例: `1.2f`）。
> - エンジン間の抽象化を保証し、名前の衝突を避けるため、DCTLの組み込み関数には通常アンダースコア（`_`）の接頭辞が必要です。

## 1. 基本的な数学関数

### 算術・クランプ
| 関数シグネチャ | 説明 |
| :--- | :--- |
| `float _fabs(float x)` | `x` の絶対値を返します。 |
| `float _fmaxf(float x, float y)` | `x` と `y` のうち、大きい方を返します。 |
| `float _fminf(float x, float y)` | `x` と `y` のうち、小さい方を返します。 |
| `float _clampf(float x, float min, float max)` | `x` を区間 `[min, max]` 内にクランプ（制限）します。 |
| `float _saturatef(float x)` | `x` を区間 `[0.0f, 1.0f]` 内にクランプします。 |
| `float _fdimf(float x, float y)` | 正の差を返します。`x > y` の場合は `x - y`、それ以外は `+0.0f`。 |
| `float _fmaf(float x, float y, float z)` | `(x * y) + z` を単一の操作として計算します（Fused Multiply-Add）。 |
| `float _copysignf(float x, float y)` | `x` の符号を `y` の符号に変更して返します。 |

### 丸め・剰余
| 関数シグネチャ | 説明 |
| :--- | :--- |
| `float _ceilf(float x)` | `x` 以上の最小の整数値を返します。 |
| `float _floorf(float x)` | `x` 以下の最大の整数値を返します。 |
| `float _truncf(float x)` | `x` の絶対値を超えない、`x` に最も近い整数値を返します。 |
| `float _round(float x)` | `x` に最も近い整数値を返します（0.5の場合は、0から遠い方に丸めます）。 |
| `float _fmod(float x, float y)` | `x / y` の浮動小数点剰余を計算します。 |

## 2. 累乗・平方根・指数関数

### 平方根・累乗
| 関数シグネチャ | 説明 |
| :--- | :--- |
| `float _powf(float x, float y)` | `x` の `y` 乗を計算します。 |
| `float _sqrtf(float x)` | `x` の非負の平方根を計算します。 |
| `float _rsqrtf(float x)` | 平方根の逆数を計算します（$1/\sqrt{x}$）。 |
| `float _hypotf(float x, float y)` | 平方和の平方根を計算します（$\sqrt{x^2 + y^2}$）。 |

### 指数・対数
| 関数シグネチャ | 説明 |
| :--- | :--- |
| `float _expf(float x)` | $e^x$ （底が $e$ の指数関数）を計算します。 |
| `float _exp2f(float x)` | $2^x$ （底が 2 の指数関数）を計算します。 |
| `float _exp10f(float x)` | $10^x$ （底が 10 の指数関数）を計算します。 |
| `float _logf(float x)` | 自然対数（$\ln x$）を計算します。 |
| `float _log2f(float x)` | 2を底とする対数（$\log_2 x$）を計算します。 |
| `float _log10f(float x)` | 10を底とする対数（$\log_{10} x$）を計算します。 |

## 3. 三角関数

### 標準三角関数
| 関数シグネチャ | 説明 |
| :--- | :--- |
| `float _cosf(float x)` | `x` の余弦（コサイン）を計算します（ラジアン）。 |
| `float _sinf(float x)` | `x` の正弦（サイン）を計算します（ラジアン）。 |
| `float _tanf(float x)` | `x` の正接（タンジェント）を計算します（ラジアン）。 |
| `float _acosf(float x)` | 逆余弦（アークコサイン）の主値を計算します。 |
| `float _asinf(float x)` | 逆正弦（アークサイン）の主値を計算します。 |
| `float _atanf(float x)` | 逆正接（アークタンジェント）の主値を計算します。 (\*) |
| `float _atan2f(float y, float x)` | 両方の引数の符号を使用して象限を決定し、`y/x` の逆正接を計算します。 |

> (\*) `_atanf` は、SDK環境で一般的に使用可能な標準的な三角関数です。

### 円周率スケール三角関数
| 関数シグネチャ | 説明 |
| :--- | :--- |
| `float _cospif(float x)` | $(x \times \pi)$ の余弦を計算します。 |
| `float _sinpif(float x)` | $(x \times \pi)$ の正弦を計算します。 |

### 双曲線関数
| 関数シグネチャ | 説明 |
| :--- | :--- |
| `float _coshf(float x)` | `x` の双曲線余弦（ハイパボリックコサイン）を計算します。 |
| `float _sinhf(float x)` | `x` の双曲線正弦（ハイパボリックサイン）を計算します。 |
| `float _tanhf(float x)` | `x` の双曲線正接（ハイパボリックタンジェント）を計算します。 |
| `float _acoshf(float x)` | `x` の逆双曲線余弦を計算します。 |
| `float _asinhf(float x)` | `x` の逆双曲線正弦を計算します。 |
| `float _atanhf(float x)` | `x` の逆双曲線正接を計算します。 |

## 4. 浮動小数点ユーティリティ

| 関数シグネチャ | 説明 |
| :--- | :--- |
| `int isinf(float x)` | `x` が無限大の場合、非ゼロの値を返します。 |
| `int isnan(float x)` | `x` が NaN (Not a Number) の場合、非ゼロの値を返します。 |
| `int signbit(float x)` | `x` の符号ビットがセットされている場合、非ゼロの値を返します。 |
| `float _fdivide(float x, float y)` | `x / y` を返します。 |
| `float _frecip(float x)` | $1 / x$ （逆数）を返します。 |
| `float _mix(T x, T y, float a)` | `(x + (y - x) * a)` を返します。`T` は `float`, `float2`, `float3`, `float4` をサポートします。`a` は `[0.0f, 1.0f]` の範囲である必要があります。 |
| `float _frexp(float x, int* exp)` | 仮数 $m \in [1/2, 1)$ を抽出し、`exp` を更新して $x = m \times 2^{exp}$ となるようにします。 |
| `float _ldexp(float x, int exp)` | $(x \times 2^{exp})$ を返します。 |

## 5. 整数数学関数

| 関数シグネチャ | 説明 |
| :--- | :--- |
| `int abs(int x)` | `x` の絶対値を返します。 |
| `int min(int x, int y)` | `x` と `y` のうち、小さい方を返します。 |
| `int max(int x, int y)` | `x` と `y` のうち、大きい方を返します。 |