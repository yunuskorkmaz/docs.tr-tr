---
title: DotNet nuget anında iletme komutu - .NET Core CLI
description: Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve onu yayımlar.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 8a64f9cdc11d03bed82a132265c3b4e1de290807
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728582"
---
# <a name="dotnet-nuget-push"></a>DotNet nuget gönderme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget push` -Sunucuya bir paket gönderir ve onu yayımlar.

## <a name="synopsis"></a>Özet

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

`dotnet nuget push` Komutu sunucuya bir paket gönderir ve onu yayımlar. Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntıları kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior). NuGet'ın varsayılan yapılandırması yükleyerek elde edilir *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), herhangi bir yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.

## <a name="arguments"></a>Arguments

`ROOT`

Edilmesini paketin dosya yolunu belirtir.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-d|--disable-buffering`

Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna iletme zaman arabelleğe almayı devre dışı bırakır.

`--force-english-output`

Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucu için API anahtarı.

`-n|--no-symbols`

Simgeler anında değil (varsa bile).

`--no-service-endpoint`

"V2/api/paketi" kaynak URL'sini append değil.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Bu seçenek sürece gereklidir `DefaultPushSource` yapılandırma değeri NuGet yapılandırma dosyasında ayarlanır.

`-sk|--symbol-api-key <API_KEY>`

Simge sunucusu için API anahtarı.

`-ss|--symbol-source <SOURCE>`

Sembol sunucu URL'sini belirtir.

`-t|--timeout <TIMEOUT>`

Saniye cinsinden bir sunucuya gönderilmesi için zaman aşımını belirtir. Varsayılan olarak 300 saniye (5 dakika). Varsayılan değer belirten 0 (sıfır saniye) uygulanır.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`-d|--disable-buffering`

Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna iletme zaman arabelleğe almayı devre dışı bırakır.

`--force-english-output`

Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucu için API anahtarı.

`-n|--no-symbols`

Simgeler anında değil (varsa bile).

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Bu seçenek sürece gereklidir `DefaultPushSource` yapılandırma değeri NuGet yapılandırma dosyasında ayarlanır.

`-sk|--symbol-api-key <API_KEY>`

Simge sunucusu için API anahtarı.

`-ss|--symbol-source <SOURCE>`

Sembol sunucu URL'sini belirtir.

`-t|--timeout <TIMEOUT>`

Saniye cinsinden bir sunucuya gönderilmesi için zaman aşımını belirtir. Varsayılan olarak 300 saniye (5 dakika). Varsayılan değer belirten 0 (sıfır saniye) uygulanır.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-d|--disable-buffering`

Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna iletme zaman arabelleğe almayı devre dışı bırakır.

`--force-english-output`

Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucu için API anahtarı.

`-n|--no-symbols`

Simgeler anında değil (varsa bile).

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Bu seçenek sürece gereklidir `DefaultPushSource` yapılandırma değeri NuGet yapılandırma dosyasında ayarlanır.

`-sk|--symbol-api-key <API_KEY>`

Simge sunucusu için API anahtarı.

`-ss|--symbol-source <SOURCE>`

Sembol sunucu URL'sini belirtir.

`-t|--timeout <TIMEOUT>`

Saniye cinsinden bir sunucuya gönderilmesi için zaman aşımını belirtir. Varsayılan olarak 300 saniye (5 dakika). Varsayılan değer belirten 0 (sıfır saniye) uygulanır.

---

## <a name="examples"></a>Örnekler

İter *foo.nupkg* varsayılan itme kaynağına bir API anahtarı belirtme:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Anında iletme *foo.nupkg* özel itme kaynağına `http://customsource`, bir API anahtarı belirtme:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

İter *foo.nupkg* varsayılan itme kaynağına:

`dotnet nuget push foo.nupkg`

İter *foo.symbols.nupkg* varsayılan simgeleri kaynağına:

`dotnet nuget push foo.symbols.nupkg`

İter *foo.nupkg* 360 saniyelik zaman aşımı varsayılan itme kaynağına belirtme:

`dotnet nuget push foo.nupkg --timeout 360`

Tüm iter *.nupkg* varsayılan itme kaynağına geçerli dizindeki dosyaları:

`dotnet nuget push *.nupkg`

Tüm iter *.nupkg* özel yapılandırma dosyanızı belirten varsayılan itme kaynağına geçerli dizindeki dosyaları *./config/My.Config*:

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
