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
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="3114e-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="3114e-103">dotnet nuget delete</span></span>

<span data-ttu-id="3114e-104">**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="3114e-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="3114e-105">Ad</span><span class="sxs-lookup"><span data-stu-id="3114e-105">Name</span></span>

<span data-ttu-id="3114e-106">`dotnet nuget delete` -Siler veya sunucu bir paketten unlists.</span><span class="sxs-lookup"><span data-stu-id="3114e-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3114e-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3114e-107">Synopsis</span></span>

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="3114e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3114e-108">Description</span></span>

<span data-ttu-id="3114e-109">`dotnet nuget delete` Komut sunucudan bir paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="3114e-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="3114e-110">İçin [nuget.org](https://www.nuget.org/), eylem paketi listeden kaldırma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3114e-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="3114e-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="3114e-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="3114e-112">Ad/silmek için paket kimliği.</span><span class="sxs-lookup"><span data-stu-id="3114e-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="3114e-113">Silmek için Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="3114e-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="3114e-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="3114e-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="3114e-115">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="3114e-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="3114e-116">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="3114e-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="3114e-117">Engellemek bir komut verir ve kimlik doğrulaması gibi işlemler için el ile gerçekleştirilen eylem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3114e-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="3114e-118">Seçeneği bu yana .NET Core 2.2 SDK kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3114e-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="3114e-119">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="3114e-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="3114e-120">"API/v2/paket" kaynak URL'ye değil.</span><span class="sxs-lookup"><span data-stu-id="3114e-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="3114e-121">Seçeneği bu yana .NET Core 2.1 SDK kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3114e-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="3114e-122">Kullanıcı girişini veya onayları için istemde değil.</span><span class="sxs-lookup"><span data-stu-id="3114e-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="3114e-123">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3114e-123">Specifies the server URL.</span></span> <span data-ttu-id="3114e-124">Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="3114e-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="3114e-125">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="3114e-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="3114e-126">Örnekler</span><span class="sxs-lookup"><span data-stu-id="3114e-126">Examples</span></span>

* <span data-ttu-id="3114e-127">Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="3114e-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="3114e-128">Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgilerini veya diğer giriş:</span><span class="sxs-lookup"><span data-stu-id="3114e-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
