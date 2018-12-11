---
title: DotNet temizleme komutu
description: Dotnet temiz komut geçerli dizinde temizler.
ms.date: 12/04/2018
ms.openlocfilehash: a25b7930794795e3dff5051a8ca1dd1b9c261dfd
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169865"
---
# <a name="dotnet-clean"></a>DotNet Temizle

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet clean` -Bir projenin çıkışı temizler.

## <a name="synopsis"></a>Özeti

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet clean` Komut önceki yapı çıkışını temizler. Olarak uygulanan bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets), projenin komut çalıştırıldığında değerlendirilir. Yalnızca derleme sırasında oluşturulan çıkışları temizlenir. Her iki Orta (*obj*) ve son çıktı (*bin*) klasörler temizlendi.

## <a name="arguments"></a>Arguments

`PROJECT`

Temizlemek için MSBuild proje. Bir proje dosyası belirtilmezse, MSBuild ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

* **`-c|--configuration {Debug|Release}`**

  Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir. Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.

* **`-f|--framework <FRAMEWORK>`**

  [Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi. Framework tanımlanmalıdır [proje dosyası](csproj.md). Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Dizini, derleme çıktılarını yerleştirilir. Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Belirtilen çalışma zamanı çıktı klasörünü siler. Bu, bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu. Seçeneği, .NET Core 2.0 SDK'sını itibaren kullanılabilir.

* **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen düzeyleri q [uiet], m [en az sıfır], [ormal] n, d [ayrıntılı] ve tanı [tanısı] ' dir.

## <a name="examples"></a>Örnekler

* Projenin varsayılan derlemeyi temizleme:

  ```console
  dotnet clean
  ```

* Yayın Yapılandırması kullanılarak oluşturulan bir projeyi Temizle:

  ```console
  dotnet clean --configuration Release
  ```