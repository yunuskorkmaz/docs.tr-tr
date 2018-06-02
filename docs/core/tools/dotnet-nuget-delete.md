---
title: DotNet nuget command - .NET Core CLI Sil
description: Dotnet nuget delete komutu siler veya sunucunun paketinden unlists.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a56ddaba72f8e1a76db810231e64993c657e908e
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697248"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="0a22e-103">DotNet nuget Sil</span><span class="sxs-lookup"><span data-stu-id="0a22e-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0a22e-104">Ad</span><span class="sxs-lookup"><span data-stu-id="0a22e-104">Name</span></span>

<span data-ttu-id="0a22e-105">`dotnet nuget delete` -Sunucudan paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="0a22e-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0a22e-106">Özet</span><span class="sxs-lookup"><span data-stu-id="0a22e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0a22e-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0a22e-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0a22e-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0a22e-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0a22e-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0a22e-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="0a22e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a22e-110">Description</span></span>

<span data-ttu-id="0a22e-111">`dotnet nuget delete` Komutu sunucu paketinden unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="0a22e-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="0a22e-112">İçin [nuget.org](https://www.nuget.org/), paket unlist için eylemdir.</span><span class="sxs-lookup"><span data-stu-id="0a22e-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="0a22e-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="0a22e-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="0a22e-114">Silmek için paket adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="0a22e-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="0a22e-115">Silmek için paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="0a22e-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="0a22e-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0a22e-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0a22e-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0a22e-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="0a22e-118">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="0a22e-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0a22e-119">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0a22e-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0a22e-120">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0a22e-120">The API key for the server.</span></span>

<span data-ttu-id="0a22e-121">` --no-service-endpoint` "V2/api/paketler" kaynak URL'sini append değil.</span><span class="sxs-lookup"><span data-stu-id="0a22e-121">` --no-service-endpoint` Doesn't append "api/v2/packages" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="0a22e-122">Kullanıcı girişi veya onayı için komut istemine değil.</span><span class="sxs-lookup"><span data-stu-id="0a22e-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0a22e-123">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a22e-123">Specifies the server URL.</span></span> <span data-ttu-id="0a22e-124">Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0a22e-124">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0a22e-125">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0a22e-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0a22e-126">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0a22e-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="0a22e-127">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="0a22e-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0a22e-128">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0a22e-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0a22e-129">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0a22e-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="0a22e-130">Kullanıcı girişi veya onayı için komut istemine değil.</span><span class="sxs-lookup"><span data-stu-id="0a22e-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0a22e-131">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a22e-131">Specifies the server URL.</span></span> <span data-ttu-id="0a22e-132">Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0a22e-132">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0a22e-133">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0a22e-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0a22e-134">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0a22e-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="0a22e-135">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="0a22e-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0a22e-136">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0a22e-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0a22e-137">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0a22e-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="0a22e-138">Kullanıcı girişi veya onayı için komut istemine değil.</span><span class="sxs-lookup"><span data-stu-id="0a22e-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0a22e-139">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a22e-139">Specifies the server URL.</span></span> <span data-ttu-id="0a22e-140">Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0a22e-140">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0a22e-141">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0a22e-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="0a22e-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0a22e-142">Examples</span></span>

<span data-ttu-id="0a22e-143">Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="0a22e-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="0a22e-144">Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgileri veya diğer giriş:</span><span class="sxs-lookup"><span data-stu-id="0a22e-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`