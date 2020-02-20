---
title: DotNet List paket komutu
description: "' DotNet List Package ' komutu bir proje veya çözümün paket başvurularını listelemek için uygun bir seçenek sağlar."
ms.date: 02/14/2020
ms.openlocfilehash: bd275c308c3a213661d5cc6c7e60817620f076a5
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503738"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,2 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet list package`-bir proje veya çözüm için paket başvurularını listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet list package` komutu, belirli bir proje veya çözüm için tüm NuGet paket başvurularını listelemek için uygun bir seçenek sağlar. Bu komutun işlemesi için gereken varlıkların olması için öncelikle projeyi derlemeniz gerekir. Aşağıdaki örnek, [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projesi için `dotnet list package` komutunun çıkışını gösterir:

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**İstenen** sütun, proje dosyasında belirtilen paket sürümünü ifade eder ve bir Aralık olabilir. **Çözümlenen** sütun, projenin şu anda kullandığı sürümü listeler ve her zaman tek bir değerdir. Adlarının hemen yanında bir `(A)` görüntüleyen paketler, proje ayarlarından (`Sdk` türü, `<TargetFramework>` veya `<TargetFrameworks>` özelliği vb.) çıkarılan [örtük paket başvurularını](csproj.md#implicit-package-references) temsil eder.

Projelerinizde kullanmakta olduğunuz paketlerin yeni sürümlerinin olup olmadığını öğrenmek için `--outdated` seçeneğini kullanın. Varsayılan olarak, çözümlenmiş sürüm aynı zamanda bir ön sürüm sürümü olmadığı takdirde, `--outdated` en son kararlı paketleri listeler. Yeni sürümler listelenirken ön sürüm sürümlerini dahil etmek için `--include-prerelease` seçeneğini de belirtin. Aşağıdaki örneklerde, önceki örnekle aynı proje için `dotnet list package --outdated --include-prerelease` komutunun çıktısı gösterilmektedir:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Projenizin geçişli bağımlılıklara sahip olup olmadığını bulmanız gerekiyorsa `--include-transitive` seçeneğini kullanın. Daha sonra başka bir pakete bağımlı olan bir paketi projenize eklediğinizde geçişli bağımlılıklar oluşur. Aşağıdaki örnek, üst düzey paketleri ve bağımlı oldukları paketleri görüntüleyen [Helloplugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projesi için `dotnet list package --include-transitive` komutunu çalıştırmanın çıkışını gösterir:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT | SOLUTION`

Üzerinde çalışılacak proje veya çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar. Birden fazla çözüm veya proje bulunursa bir hata oluşur.

## <a name="options"></a>Seçenekler

- **`--config <SOURCE>`**

  Yeni paketler aranırken kullanılacak NuGet kaynakları. `--outdated` seçeneğini gerektirir.

- **`--framework <FRAMEWORK>`**

  Yalnızca belirtilen [hedef çerçeve](../../standard/frameworks.md)için geçerli olan paketleri görüntüler. Birden çok çerçeve belirtmek için seçeneğini birden çok kez tekrarlayın. Örneğin: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--highest-minor`**

  Daha yeni paketler aranırken yalnızca eşleşen bir ana sürüm numarası olan paketleri dikkate alır. `--outdated` seçeneğini gerektirir.

- **`--highest-patch`**

  Yeni paketleri ararken yalnızca eşleşen büyük ve küçük sürüm numaralarına sahip paketleri dikkate alır. `--outdated` seçeneğini gerektirir.

- **`--include-prerelease`**

  Yeni paketleri ararken paketleri ön sürüm sürümlerini kabul eder. `--outdated` seçeneğini gerektirir.

- **`--include-transitive`**

  Üst düzey paketlerin yanı sıra geçişli paketleri listeler. Bu seçeneği belirtirken, üst düzey paketlerin bağımlı olduğu paketlerin bir listesini alırsınız.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--outdated`**

  Daha yeni sürümleri bulunan paketleri listeler.

- **`-s|--source <SOURCE>`**

  Yeni paketler aranırken kullanılacak NuGet kaynakları. `--outdated` seçeneğini gerektirir.

## <a name="examples"></a>Örnekler

- Belirli bir projenin paket başvurularını listeleyin:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- Ön sürüm sürümleri dahil olmak üzere daha yeni sürümlere sahip paket başvurularını listeleyin:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- Belirli bir hedef çerçeve için paket başvurularını listeleyin:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
