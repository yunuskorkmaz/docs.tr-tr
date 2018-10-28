---
title: DotNet nuget command - .NET Core CLI Sil
description: Dotnet-nuget-delete komutu siler veya sunucu bir paketten unlists.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: f4aa027a465c4adea1de13853063d03e8e295411
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180889"
---
# <a name="dotnet-nuget-delete"></a>DotNet nuget Sil

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget delete` -Siler veya sunucu bir paketten unlists.

## <a name="synopsis"></a>Özeti

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

`dotnet nuget delete` Komut sunucudan bir paket unlists veya siler. İçin [nuget.org](https://www.nuget.org/), eylem paketi listeden kaldırma sağlamaktır.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Ad/silmek için paket kimliği.

`PACKAGE_VERSION`

Silmek için Paket sürümü.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--force-english-output`

 Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucusu için API anahtarı.

`--no-service-endpoint` "API/v2/paket" kaynak URL'ye değil.

`--non-interactive`

Kullanıcı girişini veya onayları için istemde değil.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--force-english-output`

 Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucusu için API anahtarı.

`--non-interactive`

Kullanıcı girişini veya onayları için istemde değil.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--force-english-output`

 Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-k|--api-key <API_KEY>`

Sunucusu için API anahtarı.

`--non-interactive`

Kullanıcı girişini veya onayları için istemde değil.

`-s|--source <SOURCE>`

Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

---

## <a name="examples"></a>Örnekler

Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgilerini veya diğer giriş:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
