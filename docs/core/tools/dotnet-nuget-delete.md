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
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="0800d-103">DotNet nuget Sil</span><span class="sxs-lookup"><span data-stu-id="0800d-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0800d-104">Ad</span><span class="sxs-lookup"><span data-stu-id="0800d-104">Name</span></span>

<span data-ttu-id="0800d-105">`dotnet nuget delete` -Sunucudan paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="0800d-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0800d-106">Özet</span><span class="sxs-lookup"><span data-stu-id="0800d-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0800d-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0800d-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0800d-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0800d-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0800d-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0800d-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="0800d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0800d-110">Description</span></span>

<span data-ttu-id="0800d-111">`dotnet nuget delete` Komutu sunucu paketinden unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="0800d-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="0800d-112">İçin [nuget.org](https://www.nuget.org/), paket unlist için eylemdir.</span><span class="sxs-lookup"><span data-stu-id="0800d-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="0800d-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="0800d-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="0800d-114">Silmek için paket adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="0800d-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="0800d-115">Silmek için paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="0800d-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="0800d-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0800d-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0800d-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0800d-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="0800d-118">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="0800d-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0800d-119">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0800d-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0800d-120">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0800d-120">The API key for the server.</span></span>

<span data-ttu-id="0800d-121">`--no-service-endpoint` "V2/api/paketi" kaynak URL'sini append değil.</span><span class="sxs-lookup"><span data-stu-id="0800d-121">`--no-service-endpoint` Doesn't append "api/v2/package" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="0800d-122">Kullanıcı girişi veya onayı için komut istemine değil.</span><span class="sxs-lookup"><span data-stu-id="0800d-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0800d-123">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0800d-123">Specifies the server URL.</span></span> <span data-ttu-id="0800d-124">Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0800d-124">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0800d-125">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0800d-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0800d-126">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0800d-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="0800d-127">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="0800d-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0800d-128">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0800d-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0800d-129">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0800d-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="0800d-130">Kullanıcı girişi veya onayı için komut istemine değil.</span><span class="sxs-lookup"><span data-stu-id="0800d-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0800d-131">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0800d-131">Specifies the server URL.</span></span> <span data-ttu-id="0800d-132">Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0800d-132">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0800d-133">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0800d-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0800d-134">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0800d-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="0800d-135">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="0800d-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0800d-136">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0800d-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0800d-137">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0800d-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="0800d-138">Kullanıcı girişi veya onayı için komut istemine değil.</span><span class="sxs-lookup"><span data-stu-id="0800d-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0800d-139">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0800d-139">Specifies the server URL.</span></span> <span data-ttu-id="0800d-140">Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0800d-140">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0800d-141">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0800d-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="0800d-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0800d-142">Examples</span></span>

<span data-ttu-id="0800d-143">Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="0800d-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="0800d-144">Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgileri veya diğer giriş:</span><span class="sxs-lookup"><span data-stu-id="0800d-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
