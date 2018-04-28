---
title: DotNet nuget command - .NET Core CLI Sil
description: Dotnet nuget delete komutu siler veya sunucunun paketinden unlists.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 1e81501d526ae92336b808f98c7c192b55e89f98
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="0fb58-103">DotNet nuget Sil</span><span class="sxs-lookup"><span data-stu-id="0fb58-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0fb58-104">Ad</span><span class="sxs-lookup"><span data-stu-id="0fb58-104">Name</span></span>

<span data-ttu-id="0fb58-105">`dotnet nuget delete` -Sunucudan paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="0fb58-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0fb58-106">Özet</span><span class="sxs-lookup"><span data-stu-id="0fb58-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="0fb58-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fb58-107">Description</span></span>

<span data-ttu-id="0fb58-108">`dotnet nuget delete` Komutu sunucu paketinden unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="0fb58-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="0fb58-109">İçin [nuget.org](https://www.nuget.org/), paket unlist için eylemdir.</span><span class="sxs-lookup"><span data-stu-id="0fb58-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="0fb58-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="0fb58-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="0fb58-111">Silmek için paket.</span><span class="sxs-lookup"><span data-stu-id="0fb58-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="0fb58-112">Silmek için paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="0fb58-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="0fb58-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0fb58-113">Options</span></span>

`-h|--help`

<span data-ttu-id="0fb58-114">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0fb58-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0fb58-115">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0fb58-115">Specifies the server URL.</span></span> <span data-ttu-id="0fb58-116">Nuget.org eklemek için URL'leri desteklenen `http://www.nuget.org`, `http://www.nuget.org/api/v3`, ve `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0fb58-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0fb58-117">Özel akışları için ana bilgisayar adını değiştirin (örneğin, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0fb58-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="0fb58-118">Kullanıcı girişi veya onayı için komut istemine değil.</span><span class="sxs-lookup"><span data-stu-id="0fb58-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0fb58-119">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0fb58-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="0fb58-120">Zorlar komut satırı, İngilizce çıktı.</span><span class="sxs-lookup"><span data-stu-id="0fb58-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="0fb58-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0fb58-121">Examples</span></span>

<span data-ttu-id="0fb58-122">Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="0fb58-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="0fb58-123">Paketin 1.0 sürümü siler `Microsoft.AspNetCore.Mvc`, kullanıcıdan istemeden olmayan kimlik bilgileri veya diğer giriş:</span><span class="sxs-lookup"><span data-stu-id="0fb58-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`