# GC Runtime バイナリ

GeoConic、GC Server などの動作を保証する Java ランタイム「GC Runtime」の、ダウンロード用の ZIP です。
Adoptium（Temurin）のソースに、修正を加えて、ビルドしたものです。

## ダウンロード

ZIP は、[Releases](https://github.com/informatix-inc/GC-Runtime-Binaries/releases) に、バージョンごとに置いています。

| Java | バージョン | ベース | 証明書の脆弱性（CVE-2026-91403） | Release |
|---|---|---|---|---|
| 8 | 1.8.0_014 | jdk8u512-ga（Adoptium 8u512-b09 と同じコミット） | 対応済み | [1.8.0_014](https://github.com/informatix-inc/GC-Runtime-Binaries/releases/tag/1.8.0_014) |
| 8 | 1.8.0_013 | jdk8u504-ga（Adoptium 8u504-b01） | 対応済み | [1.8.0_013](https://github.com/informatix-inc/GC-Runtime-Binaries/releases/tag/1.8.0_013) |
| 21 | 21.0.13.0.3_008 | jdk-21.0.13.0.3-ga | 対応済み | [21.0.13.0.3_008](https://github.com/informatix-inc/GC-Runtime-Binaries/releases/tag/21.0.13.0.3_008) |
| 21 | 21.0.12.1_007 | 21.0.12.1+1 | 対応済み | [21.0.12.1_007](https://github.com/informatix-inc/GC-Runtime-Binaries/releases/tag/21.0.12.1_007) |

- 1.8.0_013、21.0.12.1_007 でも、証明書の脆弱性（CVE-2026-91403）の対応は行っています。1.8.0_014、21.0.13.0.3_008 への更新は、急ぎではありません。
- これより古い GC Runtime は、この脆弱性に対応していません。

## ZIP の選び方

名前は、`GCRuntime_<バージョン>_<Server64 または Client32>_<JRE または JDK>.zip` です。

| 名前の部分 | 内容 |
|---|---|
| Server64 | 64 ビット版（Server VM） |
| Client32 | 32 ビット版（Client VM） |
| JRE | 実行用（`j2re-image`） |
| JDK | 開発用（`j2sdk-image`。コンパイラなどを含む） |

- JavaFX（OpenJFX）は、含みません。
- Java 21 の 32 ビット版（Client32）は、OpenJDK 側で、Windows の 32 ビット版の対応が、非推奨になっています（将来、削除される可能性があります）。

## 使い方

1. ZIP を、任意のフォルダに展開します（インストーラーはありません）。
2. 展開したフォルダの `bin\java.exe` で、起動します。
3. `java -version` の例：
   - Java 8：`gc version "1.8.0-014"`
   - Java 21：`gc version "21.0.13.0.3-008"`

## ダウンロードの確認（SHA-256）

各 Release に、`SHA256SUMS.txt` を添付しています。PowerShell で、次のように、確認できます。

```
Get-FileHash -Algorithm SHA256 .\GCRuntime_1.8.0_014_Server64_JRE.zip
```

表示された値を、`SHA256SUMS.txt` の同じ ZIP の値と、見比べてください。

## ソース

| 対象 | 場所 |
|---|---|
| Java 8（GC Runtime） | [informatix-inc/GC-Runtime](https://github.com/informatix-inc/GC-Runtime) |
| Java 21（GC Runtime） | [informatix-inc/GC-Runtime21](https://github.com/informatix-inc/GC-Runtime21) |
| Adoptium（Java 8） | https://github.com/adoptium/jdk8u |
| Adoptium（Java 21） | https://github.com/adoptium/jdk21u |

## ライセンス

GPL-2.0（Classpath 例外付き）です。各 ZIP に、`LICENSE`、`ASSEMBLY_EXCEPTION`、`THIRD_PARTY_README` が含まれています。
