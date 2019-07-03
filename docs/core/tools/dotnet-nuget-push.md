---
title: DotNet nuget anında iletme komutu
description: Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve belgeyi yayımlar.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4d5efa94c6a4494158aea447be98256d2a307cd6
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539138"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget push` -Sunucuya bir paket gönderir ve belgeyi yayımlar.

## <a name="synopsis"></a>Synopsis

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget push` Komutu, yayımlar ve sunucuya bir paket gönderir. Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntılarını kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior). NuGet'ın varsayılan yapılandırmayı yükleyerek elde *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), tüm yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.

## <a name="arguments"></a>Arguments

* **`ROOT`**

  İtilecek paket dosya yolunu belirtir.

## <a name="options"></a>Seçenekler

* **`-d|--disable-buffering`**

  Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.

* **`--force-english-output`**

  Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

* **`-h|--help`**

Komut için kısa bir Yardım yazdırır.

* **`--interactive`**

  Engellemek bir komut verir ve kimlik doğrulaması gibi işlemler için el ile gerçekleştirilen eylem gerektirir. Seçeneği bu yana .NET Core 2.2 SDK kullanılabilir.

* **`-k|--api-key <API_KEY>`**

  Sunucusu için API anahtarı.

* **`-n|--no-symbols`**

  Semboller gönderin değil (hatta varsa).

* **`--no-service-endpoint`**

  "API/v2/paket" kaynak URL'ye değil. Seçeneği bu yana .NET Core 2.1 SDK kullanılabilir.

* **`-s|--source <SOURCE>`**

  Sunucu URL'sini belirtir. Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.

* **`-sk|--symbol-api-key <API_KEY>`**

  Sembol sunucusu için API anahtarı.

* **`-ss|--symbol-source <SOURCE>`**

  Sembol sunucusu URL'sini belirtir.

* **`-t|--timeout <TIMEOUT>`**

  Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir. Varsayılan olarak 300 saniyedir (5 dakika). Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.

## <a name="examples"></a>Örnekler

* Gönderim *foo.nupkg* varsayılan anında iletme kaynağı için bir API anahtarı belirtme:

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* Anında iletme *foo.nupkg* özel anında iletme kaynağına `https://customsource`, bir API anahtarı belirtme:

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* Gönderim *foo.nupkg* varsayılan anında iletme kaynağı:

  ```console
  dotnet nuget push foo.nupkg
  ```

* Gönderim *foo.symbols.nupkg* varsayılan simgeleri kaynağı:

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* Gönderim *foo.nupkg* varsayılan anında iletme kaynağına 360 saniyelik zaman aşımı belirtme:

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* Tüm göndermeler *.nupkg* varsayılan anında iletme kaynağına geçerli dizindeki dosyaları:

  ```console
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > Bu komut işe yaramazsa, (.NET Core 2.1 SDK ve önceki sürümler) SDK'ın eski sürümlerinde var olan bir hata nedeniyle olabilir.
  > Bu sorunu gidermek için SDK sürümünüzü yükseltin veya bunun yerine aşağıdaki komutu çalıştırın: `dotnet nuget push **/*.nupkg`
