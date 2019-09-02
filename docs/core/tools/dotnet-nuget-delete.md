---
title: DotNet NuGet Delete komutu
description: DotNet-NuGet-Delete komutu sunucudan bir paketi siler veya listesini kaldırır.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 70316a0baa2cf9923738a53af561b5c77014c3ff
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202576"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget delete`-Sunucudan bir paketi siler veya listesini kaldırır.

## <a name="synopsis"></a>Özeti

```console
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget delete` Komutu sunucusundan bir paketi siler veya listesini kaldırır. [NuGet.org](https://www.nuget.org/)için eylem, paketin listesini kaldırdır.

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

  Sunucu URL 'sini belirtir. NuGet.org için desteklenen URL 'ler `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`içerir. Özel akışlar için ana bilgisayar adını (örneğin, `%hostname%/api/v3`) değiştirin.

## <a name="examples"></a>Örnekler

* Paketin `Microsoft.AspNetCore.Mvc`1,0 sürümünü siler:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Paketin `Microsoft.AspNetCore.Mvc`1,0 sürümünü siler, kimlik bilgilerini veya diğer girişleri kullanıcıya sormadan:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
