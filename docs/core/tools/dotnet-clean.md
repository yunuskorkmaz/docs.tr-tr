---
title: dotnet temiz komutu
description: Dotnet temiz komutu geçerli dizini temizler.
ms.date: 02/14/2020
ms.openlocfilehash: a59922feba75e940a5cee2dfeb500f4f86372870
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463697"
---
# <a name="dotnet-clean"></a>dotnet clean

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet clean`- Projenin çıktısını temizler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--interactive]
    [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]

dotnet clean -h|--help
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
