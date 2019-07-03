---
title: DotNet nuget delete komutu
description: Dotnet-nuget-delete komutu siler veya sunucu bir paketten unlists.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0b2ba64b70bae5e06f213457e30fedeca26a9819
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539247"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget delete` -Siler veya sunucu bir paketten unlists.

## <a name="synopsis"></a>Synopsis

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget delete` Komut sunucudan bir paket unlists veya siler. İçin [nuget.org](https://www.nuget.org/), eylem paketi listeden kaldırma sağlamaktır.

## <a name="arguments"></a>Arguments

* **`PACKAGE_NAME`**

  Ad/silmek için paket kimliği.

* **`PACKAGE_VERSION`**

  Silmek için Paket sürümü.

## <a name="options"></a>Seçenekler

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

## <a name="examples"></a>Örnekler

* Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgilerini veya diğer giriş:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
