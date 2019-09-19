---
title: DotNet NuGet Delete komutu
description: DotNet-NuGet-Delete komutu sunucudan bir paketi siler veya listesini kaldırır.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 79634baa9d6d7ff1f388f6a794ffd816687be105
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117643"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget delete`-Sunucudan bir paketi siler veya listesini kaldırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
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

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Paketin `Microsoft.AspNetCore.Mvc`1,0 sürümünü siler, kimlik bilgilerini veya diğer girişleri kullanıcıya sormadan:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
