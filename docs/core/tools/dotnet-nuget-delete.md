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
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="7f494-103">DotNet nuget Sil</span><span class="sxs-lookup"><span data-stu-id="7f494-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7f494-104">Ad</span><span class="sxs-lookup"><span data-stu-id="7f494-104">Name</span></span>

<span data-ttu-id="7f494-105">`dotnet nuget delete` -Siler veya sunucu bir paketten unlists.</span><span class="sxs-lookup"><span data-stu-id="7f494-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7f494-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="7f494-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="7f494-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="7f494-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="7f494-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="7f494-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7f494-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="7f494-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="7f494-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f494-110">Description</span></span>

<span data-ttu-id="7f494-111">`dotnet nuget delete` Komut sunucudan bir paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="7f494-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="7f494-112">İçin [nuget.org](https://www.nuget.org/), eylem paketi listeden kaldırma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7f494-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="7f494-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="7f494-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="7f494-114">Ad/silmek için paket kimliği.</span><span class="sxs-lookup"><span data-stu-id="7f494-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="7f494-115">Silmek için Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="7f494-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="7f494-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7f494-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="7f494-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="7f494-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="7f494-118">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="7f494-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="7f494-119">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7f494-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="7f494-120">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="7f494-120">The API key for the server.</span></span>

<span data-ttu-id="7f494-121">`--no-service-endpoint` "API/v2/paket" kaynak URL'ye değil.</span><span class="sxs-lookup"><span data-stu-id="7f494-121">`--no-service-endpoint` Doesn't append "api/v2/package" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="7f494-122">Kullanıcı girişini veya onayları için istemde değil.</span><span class="sxs-lookup"><span data-stu-id="7f494-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="7f494-123">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f494-123">Specifies the server URL.</span></span> <span data-ttu-id="7f494-124">Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="7f494-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="7f494-125">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="7f494-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="7f494-126">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="7f494-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="7f494-127">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="7f494-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="7f494-128">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7f494-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="7f494-129">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="7f494-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="7f494-130">Kullanıcı girişini veya onayları için istemde değil.</span><span class="sxs-lookup"><span data-stu-id="7f494-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="7f494-131">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f494-131">Specifies the server URL.</span></span> <span data-ttu-id="7f494-132">Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="7f494-132">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="7f494-133">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="7f494-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7f494-134">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="7f494-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="7f494-135">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="7f494-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="7f494-136">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7f494-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="7f494-137">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="7f494-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="7f494-138">Kullanıcı girişini veya onayları için istemde değil.</span><span class="sxs-lookup"><span data-stu-id="7f494-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="7f494-139">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f494-139">Specifies the server URL.</span></span> <span data-ttu-id="7f494-140">Nuget.org eklemek için URL'leri desteklenen `https://www.nuget.org`, `https://www.nuget.org/api/v3`, ve `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="7f494-140">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="7f494-141">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="7f494-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="7f494-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7f494-142">Examples</span></span>

<span data-ttu-id="7f494-143">Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="7f494-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="7f494-144">Paketin sürümü 1.0 siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgilerini veya diğer giriş:</span><span class="sxs-lookup"><span data-stu-id="7f494-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
