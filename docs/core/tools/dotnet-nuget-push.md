---
title: DotNet NuGet Push komutu
description: DotNet NuGet Push komutu, bir paketi sunucuya gönderir ve yayınlar.
author: karann-msft
ms.date: 12/04/2019
ms.openlocfilehash: 5e80295a570adc30a06d86b6735cb0387e39d5a3
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835525"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet nuget push`-sunucuya bir paket gönderir ve onu yayımlar.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget push` komutu, bir paketi sunucuya gönderir ve yayınlar. Push komutu, sistemin NuGet yapılandırma dosyasında veya yapılandırma dosyaları zincirinde bulunan sunucu ve kimlik bilgisi ayrıntılarını kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior). NuGet 'in varsayılan yapılandırması, *%AppData%\NuGet\NuGet.config* (Windows) veya *$Home/PST local/share* (Linux/MacOS) yükleyerek elde edilir ve sürücü kökünden başlayıp geçerli dizinde sona ermek üzere herhangi bir *NuGet. config* veya *. nuget\nuget.exe* .

## <a name="arguments"></a>Arguments

* **`ROOT`**

  Gönderilecek paketin dosya yolunu belirtir.

## <a name="options"></a>Seçenekler

* **`-d|--disable-buffering`**

  Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderilirken arabelleğe almayı devre dışı bırakır.

* **`--force-english-output`**

  Uygulamayı, sabit, Ingilizce tabanlı bir kültür kullanılarak çalışmaya zorlar.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--interactive`**

  Komutun, kimlik doğrulaması gibi işlemler için el ile eylem yapmasına izin verir. .NET Core 2,2 SDK 'dan beri kullanılabilir seçeneği.

* **`-k|--api-key <API_KEY>`**

  Sunucu için API anahtarı.

* **`-n|--no-symbols`**

  Sembol (varsa bile) almaz.

* **`--no-service-endpoint`**

  Kaynak URL 'ye "API/v2/Package" eklemeyin. .NET Core 2,1 SDK 'dan beri kullanılabilir seçeneği.

* **`-s|--source <SOURCE>`**

  Sunucu URL 'sini belirtir. Bu seçenek, NuGet yapılandırma dosyasında `DefaultPushSource` config değeri ayarlanmadığı takdirde gereklidir.

* **`--skip-duplicate`**

  Bir HTTP (S) sunucusuna birden çok paket gönderdiğinizde, gönderim devam edebilmesi için 409 çakışma yanıtını uyarı olarak değerlendirir. .NET Core 3,1 SDK 'dan beri kullanılabilir.
                                 
* **`-sk|--symbol-api-key <API_KEY>`**

  Sembol sunucusu için API anahtarı.

* **`-ss|--symbol-source <SOURCE>`**

  Sembol sunucusu URL 'sini belirtir.

* **`-t|--timeout <TIMEOUT>`**

  Bir sunucuya saniye cinsinden gönderme zaman aşımını belirtir. Varsayılan değer 300 saniyedir (5 dakika). 0 (sıfır saniye) belirtilmesi varsayılan değeri uygular.

## <a name="examples"></a>Örnekler

* *Foo. nupkg* 'yi varsayılan itme kaynağına iter, bir API anahtarı belirtin:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* Bir API anahtarı belirterek, Özel gönderme kaynağına `https://customsource`*foo. nupkg* gönderin:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* *Foo. nupkg* 'yi varsayılan gönderim kaynağına iter:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* *Foo. Symbols. nupkg* 'yi varsayılan semboller kaynağına iter:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* *Foo. nupkg* 'yi varsayılan gönderim kaynağına iter, 360 saniyelik bir zaman aşımı belirterek:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* Geçerli dizindeki tüm *. nupkg* dosyalarını varsayılan gönderim kaynağına iter:

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > Bu komut işe yaramazsa, bunun nedeni SDK 'nın eski sürümlerinde var olan bir hata olabilir (.NET Core 2,1 SDK ve önceki sürümleri).
  > Bunu onarmak için SDK sürümünüzü yükseltin veya bunun yerine şu komutu çalıştırın: `dotnet nuget push **/*.nupkg`
  
* Bir HTTP (S) sunucusu tarafından 409 çakışma yanıtı döndürülse bile tüm *. nupkg* dosyalarını iter:

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
