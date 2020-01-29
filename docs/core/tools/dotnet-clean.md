---
title: DotNet temizleme komutu
description: DotNet Clean komutu geçerli dizini temizler.
ms.date: 06/26/2019
ms.openlocfilehash: 736c0bba5d156e919534f1ad811641e815b3ffac
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734244"
---
# <a name="dotnet-clean"></a>dotnet clean

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet clean`-bir projenin çıkışını temizler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet clean` komutu, önceki derleme çıkışını temizler. Bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets)olarak uygulanır, bu nedenle, komut çalıştırıldığında proje değerlendirilir. Yalnızca derleme sırasında oluşturulan çıktılar temizlenir. Ara (*obj*) ve nihai çıkış (*bin*) klasörleri temizlenir.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Temizleyen MSBuild projesi veya çözümü. Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln*ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

* **`-c|--configuration {Debug|Release}`**

  Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir. Bu seçenek yalnızca derleme zamanı sırasında belirtilmişse temizlik sırasında gereklidir.

* **`-f|--framework <FRAMEWORK>`**

  Derleme zamanında belirtilen [çerçeve](../../standard/frameworks.md) . Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır. Yapı zamanında Framework belirttiyseniz, temizleme sırasında çerçeveyi belirtmeniz gerekir.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Temizleyen derleme yapıtlarını içeren dizin. Projenin oluşturulduğu zaman çerçevesini belirttiyseniz, çıkış dizini anahtarıyla `-f|--framework <FRAMEWORK>` anahtarı belirtin.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Belirtilen çalışma zamanının çıkış klasörünü temizler. Bu, [kendinden bağımsız bir dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturulduğu zaman kullanılır. .NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyi düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Varsayılan, `normal` değeridir.

## <a name="examples"></a>Örnekler

* Projenin varsayılan derlemesini temizle:

  ```dotnetcli
  dotnet clean
  ```

* Yayın yapılandırması kullanılarak oluşturulan bir projeyi Temizleme:

  ```dotnetcli
  dotnet clean --configuration Release
  ```
