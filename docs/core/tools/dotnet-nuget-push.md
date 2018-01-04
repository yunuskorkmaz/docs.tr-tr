---
title: "DotNet nuget anında iletme komutu - .NET Core CLI"
description: "Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve onu yayımlar."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 52aac5ff1862397616287a77eac063582703d509
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-push"></a>DotNet nuget gönderme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget push`-Sunucuya bir paket gönderir ve onu yayımlar.

## <a name="synopsis"></a>Özet

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet nuget push` Komutu sunucuya bir paket gönderir ve onu yayımlar. Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntıları kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior). NuGet'ın varsayılan yapılandırması yükleyerek elde edilir *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), herhangi bir yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.

## <a name="arguments"></a>Arguments

`ROOT`

Paket ve paket sunucuya göndermek için API anahtarınıza yolunu belirtin.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Bu seçenek sürece gereklidir `DefaultPushSource` yapılandırma değeri NuGet yapılandırma dosyasında ayarlanır.

`--symbol-source <SOURCE>`

Sembol sunucu URL'sini belirtir.

`-t|--timeout <TIMEOUT>`

Saniye cinsinden bir sunucuya gönderilmesi için zaman aşımını belirtir. Varsayılan olarak 300 saniye (5 dakika). Varsayılan değer belirten 0 (sıfır saniye) uygulanır.

`-k|--api-key <API_KEY>`

Sunucu için API anahtarı.

`--symbol-api-key <API_KEY>`

Simge sunucusu için API anahtarı.

`-d|--disable-buffering`

Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna iletme zaman arabelleğe almayı devre dışı bırakır.

`-n|--no-symbols`

Simgeler anında değil (varsa bile).

`--force-english-output`

Günlüğe kaydedilen tüm çıktı İngilizce zorlar.

## <a name="examples"></a>Örnekler

İter *foo.nupkg* bir API anahtarı varsayılan itme kaynağına sağlama:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Anında iletme *foo.nupkg* özel itme kaynağına `http://customsource`, bir API anahtarı sağlama:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

İter *foo.nupkg* varsayılan itme kaynağına:

`dotnet nuget push foo.nupkg`

İter *foo.symbols.nupkg* varsayılan simgeleri kaynağına:

`dotnet nuget push foo.symbols.nupkg`

İter *foo.nupkg* 360 ikinci zaman aşımı varsayılan itme kaynağına belirtme:

`dotnet nuget push foo.nupkg --timeout 360`

Tüm iter *.nupkg* varsayılan itme kaynağına geçerli dizindeki dosyaları:

`dotnet nuget push *.nupkg`

Tüm iter *.nupkg* özel yapılandırma dosyanızı belirten varsayılan itme kaynağına geçerli dizindeki dosyaları *./config/My.Config*:

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
