---
title: DotNet NuGet Delete komutu
description: DotNet-NuGet-Delete komutu sunucudan bir paketi siler veya listesini kaldırır.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733128"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget delete`-sunucudan bir paketi siler veya listesini kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget delete` komutu sunucudan bir paketi siler veya listesini kaldırır. [NuGet.org](https://www.nuget.org/)için eylem, paketin listesini kaldırdır.

## <a name="arguments"></a>Arguments

* **`PACKAGE_NAME`**

  Silinecek paketin ad/KIMLIĞI.

* **`PACKAGE_VERSION`**

  Silinecek paketin sürümü.

## <a name="options"></a>Seçenekler

* **`--force-english-output`**

  Uygulamayı, sabit, Ingilizce tabanlı bir kültür kullanılarak çalışmaya zorlar.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--interactive`**

  Komutun, kimlik doğrulaması gibi işlemler için el ile eylem yapmasına izin verir. .NET Core 2,2 SDK 'dan beri kullanılabilir seçeneği.

* **`-k|--api-key <API_KEY>`**

  Sunucu için API anahtarı.

* **`--no-service-endpoint`**

  Kaynak URL 'ye "API/v2/Package" eklemeyin. .NET Core 2,1 SDK 'dan beri kullanılabilir seçeneği.

* **`--non-interactive`**

  Kullanıcı giriş veya teyitlerini istemez.

* **`-s|--source <SOURCE>`**

  Sunucu URL 'sini belirtir. Nuget.org için desteklenen URL 'Ler `https://www.nuget.org`, `https://www.nuget.org/api/v3`ve `https://www.nuget.org/api/v2/package`içerir. Özel akışlar için ana bilgisayar adını (örneğin, `%hostname%/api/v3`) değiştirin.

## <a name="examples"></a>Örnekler

* `Microsoft.AspNetCore.Mvc`paketinin 1,0 sürümünü siler:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* `Microsoft.AspNetCore.Mvc`paket 1,0 sürümünü siler, kullanıcıdan kimlik bilgilerini veya diğer girişleri sorma:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
