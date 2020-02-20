---
title: DotNet temizleme komutu
description: DotNet Clean komutu geçerli dizini temizler.
ms.date: 02/14/2020
ms.openlocfilehash: 186f1ea07718a8e178f88c3d079cf6e2f1f8660b
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503747"
---
# <a name="dotnet-clean"></a>dotnet clean

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet clean`-bir projenin çıkışını temizler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet clean` komutu, önceki derleme çıkışını temizler. Bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets)olarak uygulanır, bu nedenle, komut çalıştırıldığında proje değerlendirilir. Yalnızca derleme sırasında oluşturulan çıktılar temizlenir. Ara (*obj*) ve nihai çıkış (*bin*) klasörleri temizlenir.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT | SOLUTION`

Temizleyen MSBuild projesi veya çözümü. Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln*ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

* **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz. Bu seçenek yalnızca derleme zamanı sırasında belirtilmişse temizlik sırasında gereklidir.

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

  Belirtilen çalışma zamanının çıkış klasörünü temizler. Bu, [kendinden bağımsız bir dağıtım](../deploying/index.md#publish-self-contained) oluşturulduğu zaman kullanılır.

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyi düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Varsayılan değer: `normal`.

## <a name="examples"></a>Örnekler

* Projenin varsayılan derlemesini temizle:

  ```dotnetcli
  dotnet clean
  ```

* Yayın yapılandırması kullanılarak oluşturulan bir projeyi Temizleme:

  ```dotnetcli
  dotnet clean --configuration Release
  ```
