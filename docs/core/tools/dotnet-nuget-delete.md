---
title: DotNet nuget command - .NET Core CLI Sil
description: Dotnet nuget delete komutu siler veya sunucunun paketinden unlists.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 1b58136d0bc04947f0a5baba320e5e6b3e45e2f1
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728420"
---
# <a name="dotnet-nuget-delete"></a>DotNet nuget Sil

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget delete` -Sunucudan paket unlists veya siler.

## <a name="synopsis"></a>Özet

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet nuget delete` Komutu sunucu paketinden unlists veya siler. İçin [nuget.org](https://www.nuget.org/), paket unlist için eylemdir.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Silmek için paket adı/kimliği.

`PACKAGE_VERSION`

Silmek için paketin sürümü.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--force-english-output`

 Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucu için API anahtarı.

`--no-service-endpoint` "V2/api/paketi" kaynak URL'sini append değil.

`--non-interactive`

Kullanıcı girişi veya onayı için komut istemine değil.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--force-english-output`

 Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucu için API anahtarı.

`--non-interactive`

Kullanıcı girişi veya onayı için komut istemine değil.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--force-english-output`

 Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucu için API anahtarı.

`--non-interactive`

Kullanıcı girişi veya onayı için komut istemine değil.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

---

## <a name="examples"></a>Örnekler

Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgileri veya diğer giriş:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
