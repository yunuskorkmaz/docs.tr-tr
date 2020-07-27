---
title: DotNet List paket komutu
description: "' DotNet List Package ' komutu bir proje veya çözümün paket başvurularını listelemek için uygun bir seçenek sağlar."
ms.date: 02/14/2020
ms.openlocfilehash: 7157e56860936d10aa322854a589ae89e2bc0826
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164760"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,2 SDK ve sonraki sürümleri

## <a name="name"></a>Ad

`dotnet list package`-Bir proje veya çözüm için paket başvurularını listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--deprecated]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a>Açıklama

`dotnet list package`Komut belirli bir proje veya çözüm için tüm NuGet paket başvurularını listelemek için uygun bir seçenek sağlar. Bu komutun işlemesi için gereken varlıkların olması için öncelikle projeyi derlemeniz gerekir. Aşağıdaki örnek, `dotnet list package` [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projesi için komutunun çıkışını gösterir:

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**İstenen** sütun, proje dosyasında belirtilen paket sürümünü ifade eder ve bir Aralık olabilir. **Çözümlenen** sütun, projenin şu anda kullandığı sürümü listeler ve her zaman tek bir değerdir. Adlarının yanında bir doğru görüntülenen paketler, `(A)` Proje ayarlarından ( [implicit package references](csproj.md#implicit-package-references) `Sdk` tür `<TargetFramework>` veya `<TargetFrameworks>` özellik, vb.) çıkarılan örtük paket başvurularını temsil eder.

`--outdated`Projelerinizde kullanmakta olduğunuz paketlerin yeni sürümlerinin olup olmadığını öğrenmek için seçeneğini kullanın. Varsayılan olarak, `--outdated` Çözümlenmiş sürüm aynı zamanda bir ön sürüm sürümü olmadığı takdirde en son kararlı paketleri listeler. Yeni sürümler listelenirken ön sürüm sürümlerini dahil etmek için seçeneği de belirtin `--include-prerelease` . Aşağıdaki örneklerde, `dotnet list package --outdated --include-prerelease` önceki örnekle aynı proje için komutun çıktısı gösterilmektedir:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Projenizin geçişli bağımlılıklara sahip olup olmadığını bulmanız gerekiyorsa, `--include-transitive` seçeneğini kullanın. Daha sonra başka bir pakete bağımlı olan bir paketi projenize eklediğinizde geçişli bağımlılıklar oluşur. Aşağıdaki örnek, `dotnet list package --include-transitive` üst düzey paketleri ve bağımlı oldukları paketleri görüntüleyen [helloplugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projesi için komutu çalıştırmanın çıkışını gösterir:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Üzerinde çalışılacak proje veya çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar. Birden fazla çözüm veya proje bulunursa bir hata oluşur.

## <a name="options"></a>Seçenekler

- **`--config <SOURCE>`**

  Yeni paketler aranırken kullanılacak NuGet kaynakları. Seçeneğini gerektirir `--outdated` .

- **`--deprecated`**

  Kullanım dışı bırakılan paketleri görüntüler.

- **`--framework <FRAMEWORK>`**

  Yalnızca belirtilen [hedef çerçeve](../../standard/frameworks.md)için geçerli olan paketleri görüntüler. Birden çok çerçeve belirtmek için seçeneğini birden çok kez tekrarlayın. Örneğin: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--highest-minor`**

  Daha yeni paketler aranırken yalnızca eşleşen bir ana sürüm numarası olan paketleri dikkate alır. `--outdated`Veya seçeneğini gerektirir `--deprecated` .

- **`--highest-patch`**

  Yeni paketleri ararken yalnızca eşleşen büyük ve küçük sürüm numaralarına sahip paketleri dikkate alır. `--outdated`Veya seçeneğini gerektirir `--deprecated` .

- **`--include-prerelease`**

  Yeni paketleri ararken paketleri ön sürüm sürümlerini kabul eder. `--outdated`Veya seçeneğini gerektirir `--deprecated` .

- **`--include-transitive`**

  Üst düzey paketlerin yanı sıra geçişli paketleri listeler. Bu seçeneği belirtirken, üst düzey paketlerin bağımlı olduğu paketlerin bir listesini alırsınız.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--outdated`**

  Daha yeni sürümleri bulunan paketleri listeler.

- **`-s|--source <SOURCE>`**

  Yeni paketler aranırken kullanılacak NuGet kaynakları. `--outdated`Veya seçeneğini gerektirir `--deprecated` .

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
