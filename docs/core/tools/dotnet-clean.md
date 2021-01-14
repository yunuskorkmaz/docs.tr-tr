---
title: DotNet temizleme komutu
description: DotNet Clean komutu geçerli dizini temizler.
ms.date: 02/14/2020
ms.openlocfilehash: 1023f13c7662abb7dad613128631c7644ca15bb9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189609"
---
# <a name="dotnet-clean"></a>dotnet clean

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Ad

`dotnet clean` -Bir projenin çıkışını temizler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--interactive]
    [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]

dotnet clean -h|--help
```

## <a name="description"></a>Description

`dotnet clean`Komut, önceki derleme çıkışını temizler. Bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets)olarak uygulanır, bu nedenle, komut çalıştırıldığında proje değerlendirilir. Yalnızca derleme sırasında oluşturulan çıktılar temizlenir. Ara (*obj*) ve nihai çıkış (*bin*) klasörleri temizlenir.

## <a name="arguments"></a>Bağımsız değişkenler

`PROJECT | SOLUTION`

Temizleyen MSBuild projesi veya çözümü. Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln* ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

* **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz. Bu seçenek yalnızca derleme zamanı sırasında belirtilmişse temizlik sırasında gereklidir.

* **`-f|--framework <FRAMEWORK>`**

  Derleme zamanında belirtilen [çerçeve](../../standard/frameworks.md) . Çerçeve [Proje dosyasında](../project-sdk/overview.md)tanımlanmalıdır. Yapı zamanında Framework belirttiyseniz, temizleme sırasında çerçeveyi belirtmeniz gerekir.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Temizleyen derleme yapıtlarını içeren dizin. Proje oluşturulduğunda `-f|--framework <FRAMEWORK>` çerçeveyi belirttiyseniz, çıkış dizini anahtarıyla anahtarı belirtin.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Belirtilen çalışma zamanının çıkış klasörünü temizler. Bu, [kendinden bağımsız bir dağıtım](../deploying/index.md#publish-self-contained) oluşturulduğu zaman kullanılır.

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyi düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . Varsayılan değer: `normal`.

## <a name="examples"></a>Örnekler

* Projenin varsayılan derlemesini temizle:

  ```dotnetcli
  dotnet clean
  ```

* Yayın yapılandırması kullanılarak oluşturulan bir projeyi Temizleme:

  ```dotnetcli
  dotnet clean --configuration Release
  ```
