---
title: DotNet temizleme komutu
description: Dotnet temiz komut geçerli dizinde temizler.
ms.date: 06/26/2019
ms.openlocfilehash: 36630c046ff8f1ad8d513b4e64cfb74a8625776b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422013"
---
# <a name="dotnet-clean"></a>dotnet clean

**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet clean` -Bir projenin çıkışı temizler.

## <a name="synopsis"></a>Synopsis

```
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet clean` Komut önceki yapı çıkışını temizler. Olarak uygulanan bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets), projenin komut çalıştırıldığında değerlendirilir. Yalnızca derleme sırasında oluşturulan çıkışları temizlenir. Her iki Orta (*obj*) ve son çıktı (*bin*) klasörler temizlendi.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

MSBuild proje veya çözüm temizlenemedi. Bir proje veya çözüm dosyası belirtilmezse, MSBuild ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* veya *sln*ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

* **`-c|--configuration {Debug|Release}`**

  Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir. Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.

* **`-f|--framework <FRAMEWORK>`**

  [Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi. Framework tanımlanmalıdır [proje dosyası](csproj.md). Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`--interactive`**

  Durdurmak ve kullanıcı girişi ya da eylem için beklemek için komutu sağlar. Örneğin, kimlik doğrulamasını tamamlamak için. .NET Core SDK 3.0 bu yana kullanılabilir.

* **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core SDK 3.0 bu yana kullanılabilir.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Temizlemek için derleme yapıtları içeren dizin. Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Belirtilen çalışma zamanı çıktı klasörünü siler. Bu, bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu. Seçeneği, .NET Core 2.0 SDK'sını itibaren kullanılabilir.

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`. Varsayılan, `normal` değeridir.

## <a name="examples"></a>Örnekler

* Projenin varsayılan derlemeyi temizleme:

  ```console
  dotnet clean
  ```

* Yayın Yapılandırması kullanılarak oluşturulan bir projeyi Temizle:

  ```console
  dotnet clean --configuration Release
  ```
