---
title: DotNet nuget command - .NET Core CLI Sil
description: Dotnet nuget delete komutu siler veya sunucunun paketinden unlists.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 3c09556fe90a5c447b181bc1ac5b36f014399e4f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-delete"></a>DotNet nuget Sil

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget delete`-Sunucudan paket unlists veya siler.

## <a name="synopsis"></a>Özet

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet nuget delete` Komutu sunucu paketinden unlists veya siler. İçin [nuget.org](https://www.nuget.org/), paket unlist için eylemdir.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Silmek için paket.

`PACKAGE_VERSION`

Silmek için paketin sürümü.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

`--non-interactive`

Kullanıcı girişi veya onayı için komut istemine değil.

`-k|--api-key <API_KEY>`

Sunucu için API anahtarı.

`--force-english-output`

Zorlar komut satırı, İngilizce çıktı.

## <a name="examples"></a>Örnekler

Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgileri veya diğer giriş:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`