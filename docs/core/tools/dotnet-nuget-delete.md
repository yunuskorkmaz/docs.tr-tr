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
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="81098-103">DotNet nuget Sil</span><span class="sxs-lookup"><span data-stu-id="81098-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="81098-104">Ad</span><span class="sxs-lookup"><span data-stu-id="81098-104">Name</span></span>

<span data-ttu-id="81098-105">`dotnet nuget delete` -Siler veya sunucu bir paketten unlists.</span><span class="sxs-lookup"><span data-stu-id="81098-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="81098-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="81098-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="81098-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="81098-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="81098-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="81098-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="81098-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81098-109">Description</span></span>

<span data-ttu-id="81098-110">`dotnet nuget delete` Komut sunucudan bir paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="81098-110">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="81098-111">İçin [nuget.org](https://www.nuget.org/), eylem paketi listeden kaldırma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="81098-111">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="81098-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="81098-112">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="81098-113">Ad/silmek için paket kimliği.</span><span class="sxs-lookup"><span data-stu-id="81098-113">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="81098-114">Silmek için Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="81098-114">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="81098-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="81098-115">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="81098-116">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="81098-116">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`--force-english-output`**

  <span data-ttu-id="81098-117">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="81098-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="81098-118">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="81098-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="81098-119">Engellemek bir komut verir ve kimlik doğrulaması gibi işlemler için el ile gerçekleştirilen eylem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="81098-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="81098-120">Seçeneği bu yana .NET Core 2.2 SDK kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81098-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="81098-121">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="81098-121">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="81098-122">"API/v2/paket" kaynak URL'ye değil.</span><span class="sxs-lookup"><span data-stu-id="81098-122">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="81098-123">Seçeneği bu yana .NET Core 2.1 SDK kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81098-123">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="81098-124">Kullanıcı girişini veya onayları için istemde değil.</span><span class="sxs-lookup"><span data-stu-id="81098-124">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="81098-125">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="81098-125">Specifies the server URL.</span></span> <span data-ttu-id="81098-126">Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="81098-126">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="81098-127">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="81098-127">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="81098-128">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="81098-128">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`--force-english-output`**

  <span data-ttu-id="81098-129">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="81098-129">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="81098-130">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="81098-130">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="81098-131">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="81098-131">The API key for the server.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="81098-132">Kullanıcı girişini veya onayları için istemde değil.</span><span class="sxs-lookup"><span data-stu-id="81098-132">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="81098-133">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="81098-133">Specifies the server URL.</span></span> <span data-ttu-id="81098-134">Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="81098-134">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="81098-135">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="81098-135">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="81098-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="81098-136">Examples</span></span>

* <span data-ttu-id="81098-137">Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="81098-137">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="81098-138">Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgilerini veya diğer giriş:</span><span class="sxs-lookup"><span data-stu-id="81098-138">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```