---
title: DotNet nuget delete komutu
description: Dotnet-nuget-delete komutu siler veya sunucu bir paketten unlists.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: a657fa273ca6b5229a1713fbcaf003217a59fd7f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612634"
---
# <a name="dotnet-nuget-delete"></a>DotNet nuget Sil

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget delete` -Siler veya sunucu bir paketten unlists.

## <a name="synopsis"></a>Synopsis

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
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

* **`PACKAGE_NAME`**

  Ad/silmek için paket kimliği.

* **`PACKAGE_VERSION`**

  Silmek için Paket sürümü.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

* **`--force-english-output`**

  Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`--interactive`**

  Engellemek bir komut verir ve kimlik doğrulaması gibi işlemler için el ile gerçekleştirilen eylem gerektirir. Seçeneği bu yana .NET Core 2.2 SDK kullanılabilir.

* **`-k|--api-key <API_KEY>`**

  Sunucusu için API anahtarı.

* **`--no-service-endpoint`**

  "API/v2/paket" kaynak URL'ye değil. Seçeneği bu yana .NET Core 2.1 SDK kullanılabilir.

* **`--non-interactive`**

  Kullanıcı girişini veya onayları için istemde değil.

* **`-s|--source <SOURCE>`**

  Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

* **`--force-english-output`**

  Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`-k|--api-key <API_KEY>`**

  Sunucusu için API anahtarı.

* **`--non-interactive`**

  Kullanıcı girişini veya onayları için istemde değil.

* **`-s|--source <SOURCE>`**

  Sunucu URL'sini belirtir. Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`. Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).

---

## <a name="examples"></a>Örnekler

* Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgilerini veya diğer giriş:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```