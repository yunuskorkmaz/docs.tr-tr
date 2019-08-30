---
title: DotNet temizleme komutu
description: DotNet Clean komutu geçerli dizini temizler.
ms.date: 06/26/2019
ms.openlocfilehash: 113bc076b9f14a471c631801fe4a7cb1e044a411
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168054"
---
# <a name="dotnet-clean"></a>dotnet clean

**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet clean`-Bir projenin çıkışını temizler.

## <a name="synopsis"></a>Özeti

```console
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet clean` Komut, önceki derleme çıkışını temizler. Bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets)olarak uygulanır, bu nedenle, komut çalıştırıldığında proje değerlendirilir. Yalnızca derleme sırasında oluşturulan çıktılar temizlenir. Ara (*obj*) ve nihai çıkış (*bin*) klasörleri temizlenir.

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

  Temizleyen derleme yapıtlarını içeren dizin. Proje oluşturulduğunda çerçeveyi belirttiyseniz, çıkış dizini anahtarıyla anahtarıbelirtin.`-f|--framework <FRAMEWORK>`

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Belirtilen çalışma zamanının çıkış klasörünü temizler. Bu, [kendinden bağımsız bir dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturulduğu zaman kullanılır. .NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyi düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]` Varsayılan, `normal` değeridir.

## <a name="examples"></a>Örnekler

* Projenin varsayılan derlemesini temizle:

  ```console
  dotnet clean
  ```

* Yayın yapılandırması kullanılarak oluşturulan bir projeyi Temizleme:

  ```console
  dotnet clean --configuration Release
  ```
