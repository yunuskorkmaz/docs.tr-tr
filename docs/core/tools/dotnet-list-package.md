---
title: dotnet liste paket komutu
description: "'Dotnet list package' komutu, bir proje veya çözüm için paket başvurularını listelemek için kullanışlı bir seçenek sağlar."
ms.date: 02/14/2020
ms.openlocfilehash: 12d64600d178ea8cf490a0d6917e67bd3d8c6d21
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463656"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.2 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet list package`- Proje veya çözüm için paket referanslarını listeler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet list package` belirli bir proje veya çözüm için tüm NuGet paket başvurularını listelemek için kullanışlı bir seçenek sağlar. Öncelikle bu komutun işlemesi için gereken varlıklara sahip olmak için projeyi oluşturmanız gerekir. Aşağıdaki örnek, [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) `dotnet list package` projesi için komutçıktısını gösterir:

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**İstenen** sütun, proje dosyasında belirtilen paket sürümüne başvurur ve bir aralık olabilir. **Çözümlenen** sütun, projenin şu anda kullanmakta olduğu sürümü listeler ve her zaman tek bir değerdir. Adlarının yanında `(A)` bir hakkı görüntüleyen paketler, proje ayarlarınızdan (tür `<TargetFramework>` `<TargetFrameworks>` veya`Sdk` özellik, vb.) çıkarılan [örtük paket başvurularını](csproj.md#implicit-package-references) temsil eder.

Projelerinizde `--outdated` kullanmakta olduğunuz paketlerin daha yeni sürümlerinin olup olmadığını öğrenmek için seçeneği kullanın. Varsayılan olarak, `--outdated` çözülen sürüm de bir ön sürüm olmadığı sürece en son kararlı paketleri listeler. Yeni sürümleri listelerken yayın öncesi sürümleri eklemek `--include-prerelease` için de seçeneği belirtin. Aşağıdaki örnekler, önceki örnekle aynı proje için `dotnet list package --outdated --include-prerelease` komutun çıktısını gösterir:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Projenizin geçişli bağımlılıkları olup olmadığını öğrenmeniz gerekiyorsa, `--include-transitive` seçeneği kullanın. Geçişli bağımlılıklar, projenize başka bir pakete dayanan bir paket eklediğinizde oluşur. Aşağıdaki örnek, üst düzey `dotnet list package --include-transitive` paketleri ve bağlı oldukları paketleri görüntüleyen [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projesi nin komutunu çalıştıran çıktıyı gösterir:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT | SOLUTION`

İşletilmesi gereken proje veya çözüm dosyası. Belirtilmemişse, komut geçerli dizini arar. Birden fazla çözüm veya proje bulunursa, bir hata atılır.

## <a name="options"></a>Seçenekler

- **`--config <SOURCE>`**

  NuGet kaynakları yeni paketler ararken kullanmak için. `--outdated` Seçeneği gerektirir.

- **`--framework <FRAMEWORK>`**

  Yalnızca belirtilen [hedef çerçeve](../../standard/frameworks.md)için geçerli paketleri görüntüler. Birden çok çerçeve belirtmek için seçeneği birden çok kez yineleyin. Örneğin: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--highest-minor`**

  Yeni paketleri ararken yalnızca eşleşen bir ana sürüm numarasına sahip paketleri dikkate alır. `--outdated` Seçeneği gerektirir.

- **`--highest-patch`**

  Yeni paketleri ararken yalnızca eşleşen büyük ve küçük sürüm numaralarına sahip paketleri dikkate alır. `--outdated` Seçeneği gerektirir.

- **`--include-prerelease`**

  Yeni paketler ararken yayın öncesi sürümsürümlerine sahip paketleri dikkate alır. `--outdated` Seçeneği gerektirir.

- **`--include-transitive`**

  Üst düzey paketlere ek olarak geçişli paketleri listeler. Bu seçeneği belirtirken, üst düzey paketlerin bağlı olduğu paketlerin bir listesini alırsınız.

- **`--interactive`**

  Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar. Örneğin, kimlik doğrulamasını tamamlamak için. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`--outdated`**

  Yeni sürümleri olan paketleri listeler.

- **`-s|--source <SOURCE>`**

  NuGet kaynakları yeni paketler ararken kullanmak için. `--outdated` Seçeneği gerektirir.

## <a name="examples"></a>Örnekler

- Belirli bir projenin paket başvurularını listele:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- Sürüm öncesi sürümler de dahil olmak üzere daha yeni sürümleri olan paket başvurularını listele:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- Belirli bir hedef çerçeve için paket başvurularını listele:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
