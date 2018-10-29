---
title: DotNet nuget anında iletme komutu - .NET Core CLI
description: Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve belgeyi yayımlar.
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: b9c0fad886cd1234325c58bf61b1a010bce421d9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200032"
---
# <a name="dotnet-nuget-push"></a>DotNet nuget anında iletme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget push` -Sunucuya bir paket gönderir ve belgeyi yayımlar.

## <a name="synopsis"></a>Özeti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet nuget push` Komutu, yayımlar ve sunucuya bir paket gönderir. Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntılarını kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior). NuGet'ın varsayılan yapılandırmayı yükleyerek elde *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), tüm yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.

## <a name="arguments"></a>Arguments

`ROOT`

İtilecek paket dosya yolunu belirtir.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-d|--disable-buffering`

Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.

`--force-english-output`

Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucusu için API anahtarı.

`-n|--no-symbols`

Semboller gönderin değil (hatta varsa).

`--no-service-endpoint`

"API/v2/paket" kaynak URL'ye değil.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.

`-sk|--symbol-api-key <API_KEY>`

Sembol sunucusu için API anahtarı.

`-ss|--symbol-source <SOURCE>`

Sembol sunucusu URL'sini belirtir.

`-t|--timeout <TIMEOUT>`

Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir. Varsayılan olarak 300 saniyedir (5 dakika). Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`-d|--disable-buffering`

Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.

`--force-english-output`

Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucusu için API anahtarı.

`-n|--no-symbols`

Semboller gönderin değil (hatta varsa).

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.

`-sk|--symbol-api-key <API_KEY>`

Sembol sunucusu için API anahtarı.

`-ss|--symbol-source <SOURCE>`

Sembol sunucusu URL'sini belirtir.

`-t|--timeout <TIMEOUT>`

Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir. Varsayılan olarak 300 saniyedir (5 dakika). Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-d|--disable-buffering`

Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.

`--force-english-output`

Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucusu için API anahtarı.

`-n|--no-symbols`

Semboller gönderin değil (hatta varsa).

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.

`-sk|--symbol-api-key <API_KEY>`

Sembol sunucusu için API anahtarı.

`-ss|--symbol-source <SOURCE>`

Sembol sunucusu URL'sini belirtir.

`-t|--timeout <TIMEOUT>`

Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir. Varsayılan olarak 300 saniyedir (5 dakika). Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.

---

## <a name="examples"></a>Örnekler

Gönderim *foo.nupkg* varsayılan anında iletme kaynağı için bir API anahtarı belirtme:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Anında iletme *foo.nupkg* özel anında iletme kaynağına `https://customsource`, bir API anahtarı belirtme:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/`

Gönderim *foo.nupkg* varsayılan anında iletme kaynağı:

`dotnet nuget push foo.nupkg`

Gönderim *foo.symbols.nupkg* varsayılan simgeleri kaynağı:

`dotnet nuget push foo.symbols.nupkg`

Gönderim *foo.nupkg* varsayılan anında iletme kaynağına 360 saniyelik zaman aşımı belirtme:

`dotnet nuget push foo.nupkg --timeout 360`

Tüm göndermeler *.nupkg* varsayılan anında iletme kaynağına geçerli dizindeki dosyaları:

`dotnet nuget push *.nupkg`
