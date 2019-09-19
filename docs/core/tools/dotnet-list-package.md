---
title: DotNet List paket komutu
description: "' DotNet List Package ' komutu bir proje veya çözümün paket başvurularını listelemek için uygun bir seçenek sağlar."
ms.date: 06/26/2019
ms.openlocfilehash: fe95f3898c5bd85956f4312eb4d20259227e9ff0
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117732"
---
# <a name="dotnet-list-package"></a>dotnet list package

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a>Ad

`dotnet list package`-Bir proje veya çözüm için paket başvurularını listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet list package` Komut belirli bir proje veya çözüm için tüm NuGet paket başvurularını listelemek için uygun bir seçenek sağlar. Bu komutun işlemesi için gereken varlıkların olması için öncelikle projeyi derlemeniz gerekir. Aşağıdaki örnek, `dotnet list package` [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projesi için komutunun çıkışını gösterir:

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**İstenen** sütun, proje dosyasında belirtilen paket sürümünü ifade eder ve bir Aralık olabilir. **Çözümlenen** sütun, projenin şu anda kullandığı sürümü listeler ve her zaman tek bir değerdir. Adlarının yanında `(A)` bir doğru görüntülenen paketler, proje `<TargetFramework>` ayarlarından (`Sdk` tür veya `<TargetFrameworks>` özellik, vb.) çıkarılan [örtük paket başvurularını](csproj.md#implicit-package-references) temsil eder.

Projelerinizde kullanmakta olduğunuz paketlerin yeni sürümlerinin olup olmadığını öğrenmek için seçeneğinikullanın.`--outdated` Varsayılan olarak, `--outdated` çözümlenmiş sürüm aynı zamanda bir ön sürüm sürümü olmadığı takdirde en son kararlı paketleri listeler. Yeni sürümler listelenirken ön sürüm sürümlerini dahil etmek için `--include-prerelease` seçeneği de belirtin. Aşağıdaki örneklerde, önceki örnekle aynı proje için `dotnet list package --outdated --include-prerelease` komutun çıktısı gösterilmektedir:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

Projenizin geçişli bağımlılıklara sahip olup olmadığını bulmanız gerekiyorsa, `--include-transitive` seçeneğini kullanın. Daha sonra başka bir pakete bağımlı olan bir paketi projenize eklediğinizde geçişli bağımlılıklar oluşur. Aşağıdaki örnek, üst düzey paketleri ve bağımlı oldukları `dotnet list package --include-transitive` paketleri görüntüleyen [helloplugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projesi için komutu çalıştırmanın çıkışını gösterir:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Üzerinde çalışılacak proje veya çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar. Birden fazla çözüm veya proje bulunursa bir hata oluşur.

## <a name="options"></a>Seçenekler

* **`--config <SOURCE>`**

  Yeni paketler aranırken kullanılacak NuGet kaynakları. `--outdated` Seçeneğini gerektirir.

* **`--framework <FRAMEWORK>`**

  Yalnızca belirtilen [hedef çerçeve](../../standard/frameworks.md)için geçerli olan paketleri görüntüler. Birden çok çerçeve belirtmek için seçeneğini birden çok kez tekrarlayın. Örneğin: bağlanmak için yapılandırın.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--highest-minor`**

  Daha yeni paketler aranırken yalnızca eşleşen bir ana sürüm numarası olan paketleri dikkate alır. `--outdated` Seçeneğini gerektirir.

* **`--highest-patch`**

  Yeni paketleri ararken yalnızca eşleşen büyük ve küçük sürüm numaralarına sahip paketleri dikkate alır. `--outdated` Seçeneğini gerektirir.

* **`--include-prerelease`**

  Yeni paketleri ararken paketleri ön sürüm sürümlerini kabul eder. `--outdated` Seçeneğini gerektirir.

* **`--include-transitive`**

  Üst düzey paketlerin yanı sıra geçişli paketleri listeler. Bu seçeneği belirtirken, üst düzey paketlerin bağımlı olduğu paketlerin bir listesini alırsınız.

* **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`--outdated`**

  Daha yeni sürümleri bulunan paketleri listeler.

* **`-s|--source <SOURCE>`**

  Yeni paketler aranırken kullanılacak NuGet kaynakları. `--outdated` Seçeneğini gerektirir.

## <a name="examples"></a>Örnekler

* Belirli bir projenin paket başvurularını listeleyin:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

* Ön sürüm sürümleri dahil olmak üzere daha yeni sürümlere sahip paket başvurularını listeleyin:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

* Belirli bir hedef çerçeve için paket başvurularını listeleyin:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
