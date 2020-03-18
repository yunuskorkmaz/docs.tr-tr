---
title: dotnet temiz komutu
description: Dotnet temiz komutu geçerli dizini temizler.
ms.date: 02/14/2020
ms.openlocfilehash: 186f1ea07718a8e178f88c3d079cf6e2f1f8660b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503747"
---
# <a name="dotnet-clean"></a>dotnet clean

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet clean`- Projenin çıktısını temizler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet clean` önceki yapının çıktısını temizler. MSBuild [hedefi](/visualstudio/msbuild/msbuild-targets)olarak uygulandığından, komut çalıştırıldığında proje değerlendirilir. Yalnızca yapı sırasında oluşturulan çıktılar temizlenir. Hem ara *(obj)* hem de son çıktı *(bin)* klasörleri temizlenir.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT | SOLUTION`

MSBuild projesi veya çözüm temizlemek için. Bir proje veya çözüm dosyası belirtilmemişse, MSBuild *proj* veya *sln*ile biten ve bu dosyayı kullanan bir dosya uzantısı olan bir dosya için geçerli çalışma dizinini arar.

## <a name="options"></a>Seçenekler

* **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz. Bu seçenek yalnızca yapı süresi içinde belirttiğiniz zaman temizlik yaparken gereklidir.

* **`-f|--framework <FRAMEWORK>`**

  Oluşturma zamanında belirtilen [çerçeve.](../../standard/frameworks.md) Çerçeve [proje dosyasında](csproj.md)tanımlanmalıdır. Çerçeveyi oluşturma zamanında belirttiyseniz, temizleme sırasında çerçeveyi belirtmeniz gerekir.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--interactive`**

  Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar. Örneğin, kimlik doğrulamasını tamamlamak için. .NET Core 3.0 SDK'dan beri mevcuttur.

* **`--nologo`**

  Başlangıç bayrağını veya telif hakkı iletisini görüntülemez. .NET Core 3.0 SDK'dan beri mevcuttur.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Temizlemek için yapı yapıları içeren dizin. Proje `-f|--framework <FRAMEWORK>` oluşturulurken çerçeveyi belirttiyseniz, çıkış dizin anahtarıyla anahtarı belirtin.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Belirtilen çalışma zamanının çıktı klasörünü temizler. Bu, bağımsız bir [dağıtım](../deploying/index.md#publish-self-contained) oluşturulduğunda kullanılır.

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `normal`.

## <a name="examples"></a>Örnekler

* Projenin varsayılan yapısını temizleyin:

  ```dotnetcli
  dotnet clean
  ```

* Sürüm yapılandırması kullanılarak oluşturulmuş bir projeyi temizleme:

  ```dotnetcli
  dotnet clean --configuration Release
  ```
