---
title: DotNet NuGet Push komutu
description: DotNet NuGet Push komutu, bir paketi sunucuya gönderir ve yayınlar.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 50a4a542c2d192bfbd927845489d04fd1b6c6cf3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555129"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Ad

`dotnet nuget push`-Sunucuya bir paket gönderir ve onu yayımlar.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols true]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a>Açıklama

`dotnet nuget push`Komut, bir paketi sunucuya gönderir ve yayınlar. Push komutu, sistemin NuGet yapılandırma dosyasında veya yapılandırma dosyaları zincirinde bulunan sunucu ve kimlik bilgisi ayrıntılarını kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior). NuGet 'in varsayılan yapılandırması, *% AppData% \NuGet\NuGet.config* (Windows) veya *$Home/PST local/share* (Linux/MacOS) yüklenirken ve sürücü kökünden başlayıp geçerli dizinde sona ermek üzere herhangi bir *nuget.config* veya *.nuget\nuget.config* yükleyerek elde edilir.

Komut, var olan bir paketi iter. Paket oluşturmaz. Bir paket oluşturmak için kullanın [`dotnet pack`](dotnet-pack.md) .

## <a name="arguments"></a>Arguments

- **`ROOT`**

  Gönderilecek paketin dosya yolunu belirtir.

## <a name="options"></a>Seçenekler

- **`-d|--disable-buffering`**

  Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderilirken arabelleğe almayı devre dışı bırakır.

- **`--force-english-output`**

  Uygulamayı, sabit, Ingilizce tabanlı bir kültür kullanılarak çalışmaya zorlar.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun, kimlik doğrulaması gibi işlemler için el ile eylem yapmasına izin verir. .NET Core 2,2 SDK 'dan beri kullanılabilir seçeneği.

- **`-k|--api-key <API_KEY>`**

  Sunucu için API anahtarı.

- **`-n|--no-symbols true`**

  Sembol (varsa bile) almaz.

- **`--no-service-endpoint`**

  Kaynak URL 'ye "API/v2/Package" eklemeyin. .NET Core 2,1 SDK 'dan beri kullanılabilir seçeneği.

- **`-s|--source <SOURCE>`**

  Sunucu URL 'sini belirtir. Bu seçenek, `DefaultPushSource` NuGet yapılandırma dosyasında yapılandırma değeri ayarlanmadığı takdirde gereklidir.

- **`--skip-duplicate`**

  Bir HTTP (S) sunucusuna birden çok paket gönderdiğinizde, gönderim devam edebilmesi için 409 çakışma yanıtını uyarı olarak değerlendirir. .NET Core 3,1 SDK 'dan beri kullanılabilir.

- **`-sk|--symbol-api-key <API_KEY>`**

  Sembol sunucusu için API anahtarı.

- **`-ss|--symbol-source <SOURCE>`**

  Sembol sunucusu URL 'sini belirtir.

- **`-t|--timeout <TIMEOUT>`**

  Bir sunucuya saniye cinsinden gönderme zaman aşımını belirtir. Varsayılan değer 300 saniyedir (5 dakika). 0 (sıfır saniye) belirtilmesi varsayılan değeri uygular.

## <a name="examples"></a>Örnekler

- Bir API anahtarı belirterek, varsayılan gönderim kaynağına *foo. nupkg* gönderin:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- Bir API anahtarı belirterek, resmi NuGet sunucusuna *foo. nupkg* gönderin:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Bir API anahtarı belirterek, özel itme kaynağına *foo. nupkg* gönderin `https://customsource` :

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- *Foo. nupkg* 'yi varsayılan gönderim kaynağına gönder:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- Varsayılan semboller kaynağına *foo. Symbols. nupkg* gönder:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- Varsayılan itme kaynağına *foo. nupkg* göndererek 360 saniyelik bir zaman aşımı belirtin:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- Geçerli dizindeki tüm *. nupkg* dosyalarını varsayılan gönderim kaynağına gönder:

  ```dotnetcli
  dotnet nuget push "*.nupkg"
  ```

  > [!NOTE]
  > Bu komut işe yaramazsa, bunun nedeni SDK 'nın eski sürümlerinde var olan bir hata olabilir (.NET Core 2,1 SDK ve önceki sürümleri).
  > Bunu onarmak için SDK sürümünüzü yükseltin veya bunun yerine aşağıdaki komutu çalıştırın:`dotnet nuget push "**/*.nupkg"`
  
  > [!NOTE]
  > Kapsayan alıntılar, glob dosyasını gerçekleştiren Bash gibi kabuklar için gereklidir. Daha fazla bilgi için bkz. [NuGet/Home # 4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120).

- Bir HTTP (S) sunucusu tarafından 409 çakışma yanıtı döndürülse bile tüm *. nupkg* dosyalarını gönderin:

  ```dotnetcli
  dotnet nuget push "*.nupkg" --skip-duplicate
  ```

- Geçerli dizindeki tüm *. nupkg* dosyalarını yerel akış dizinine gönder:

  ```dotnetcli
  dotnet nuget push "*.nupkg" -s c:\mydir
  ```

  Bu komut, paketleri hiyerarşik bir klasör yapısında depolamaz, bu da performansı iyileştirmek için önerilir. Daha fazla bilgi için bkz. [Yerel akışlar](/nuget/hosting-packages/local-feeds).  
