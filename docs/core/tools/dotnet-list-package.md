---
title: DotNet Listele paket komutu
description: "'Dotnet paket listeleme' komutu, bir proje veya çözüm için paket referanslarını listelemek için uygun bir seçenek sağlar."
ms.date: 04/09/2019
ms.openlocfilehash: bc38b94201f85ed4b22e11722ef5cabcb6fbf040
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481600"
---
# <a name="dotnet-list-package"></a>DotNet paket listeleme

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a>Ad

`dotnet list package` -Bir proje veya çözüm için paket başvuruları listeler.

## <a name="synopsis"></a>Synopsis

```
dotnet list [<PROJECT | SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet list package` Komut belirli bir proje veya çözüm için NuGet paket başvuruları tüm listelemek için uygun bir seçenek sağlar. Önce bu komutu işlemek gerekli varlıkları için projeyi derlemek gerekir. Aşağıdaki örnek, çıktısını gösterir `dotnet list package` komutunu [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) proje:

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**İstenen** sütun proje dosyasında belirtilen Paket sürümü ifade eder ve bir aralık olabilir. **Çözümlenmiş** proje şu anda kullanıyor ve her zaman tek bir değer olan sürüm sütununda listelenir. Görüntüleme paketleri bir `(A)` sağ adlarının yanındaki temsil [örtük paket başvuruları](csproj.md#implicit-package-references) proje ayarlarınızdan çıkarılan (`Sdk` türü `<TargetFramework>` veya `<TargetFrameworks>` özelliği, vb..)

Kullanım `--outdated` projelerinizde kullandığınız paketlerin daha yeni sürümlerin olup olmadığını öğrenmek için seçeneği. Varsayılan olarak, `--outdated` çözümlenen sürümünü bir ön sürümünü de olmadığı sürece, en son kararlı paketler listeler. Daha yeni sürümlerin listelenmesi zaman ön sürümleri dahil etmek için de belirtmeniz `--include-prerelease` seçeneği. Aşağıdaki örnekler çıktısını gösterir `dotnet list package --outdated --include-prerelease` komut önceki örnekteki gibi aynı proje için:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

Projenizi geçişli bağımlılıkları, kullanım olup olmadığını bulmak gereken `--include-transitive` seçeneği. Sırayla başka bir pakete bağlıdır. projenize bir paket eklerken, geçişli bağımlılıkları oluşur. Aşağıdaki örnek çalışan çıktısında `dotnet list package --include-transitive` komutunu [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) en üst düzey paketleri ve bunların bağlı olduğu paketler görüntüleyen proje:

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

Üzerinde çalışılacak proje veya çözüm dosyası. Belirtilmezse, komut için geçerli dizinde arar. Birden fazla çözüm ya da proje bulunursa, bir hata oluşturulur.

## <a name="options"></a>Seçenekler

* **`--config <SOURCE>`**

  Yeni paketleri aramak için kullanılan NuGet kaynakları. Gerektirir `--outdated` seçeneği.

* **`--framework <FRAMEWORK>`**

  Yalnızca belirtilen geçerli paketleri görüntüler [hedef Framework'ü](../../standard/frameworks.md). Birden çok çerçeveyi belirtmek için bu seçeneği birden çok kez yineleyin. Örneğin: `--framework netcoreapp2.2 --framework netstandard2.0`

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`--highest-minor`**

  Paketler yalnızca eşleşen bir ana sürüm numarası ile yeni paketler için arama yaparken göz önünde bulundurur. Gerektirir `--outdated` seçeneği.

* **`--highest-patch`**

  Yalnızca eşleşen paketleri büyük ve küçük sürüm numaraları için yeni paketler arama yaparken göz önünde bulundurur. Gerektirir `--outdated` seçeneği.

* **`--include-prerelease`**

  Yayın öncesi sürümler paketlerle yeni paketler için arama yaparken göz önünde bulundurur. Gerektirir `--outdated` seçeneği.

* **`--include-transitive`**

  Üst düzey paketlerinin yanı sıra geçişli paketleri listeler. Bu seçeneği belirtmek, üst düzey paketleri bağımlı paketlerin listesini alın.

* **`--outdated`**

  Yeni sürümler kullanılabilir olan paketleri listeler.

* **`-s|--source <SOURCE>`**

  Yeni paketleri aramak için kullanılan NuGet kaynakları. Gerektirir `--outdated` seçeneği.

## <a name="examples"></a>Örnekler

* Belirli bir projenin paket başvuruları listesi:

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* Ön sürümleri dahil olmak üzere, kullanılabilir yeni sürümlere sahip paket başvuruları listesi:

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* Belirli hedef çerçeve için paket başvuruları listeleyin:

  ```console
  dotnet list package --framework netcoreapp3.0
  ```