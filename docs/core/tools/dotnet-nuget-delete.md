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
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="47329-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="47329-103">dotnet nuget delete</span></span>

<span data-ttu-id="47329-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="47329-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="47329-105">Ad</span><span class="sxs-lookup"><span data-stu-id="47329-105">Name</span></span>

<span data-ttu-id="47329-106">`dotnet nuget delete`-sunucudan bir paketi siler veya listesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="47329-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="47329-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="47329-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="47329-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47329-108">Description</span></span>

<span data-ttu-id="47329-109">`dotnet nuget delete` komutu sunucudan bir paketi siler veya listesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="47329-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="47329-110">[NuGet.org](https://www.nuget.org/)için eylem, paketin listesini kaldırdır.</span><span class="sxs-lookup"><span data-stu-id="47329-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="47329-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="47329-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="47329-112">Silinecek paketin ad/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="47329-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="47329-113">Silinecek paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="47329-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="47329-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="47329-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="47329-115">Uygulamayı, sabit, Ingilizce tabanlı bir kültür kullanılarak çalışmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="47329-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="47329-116">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="47329-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="47329-117">Komutun, kimlik doğrulaması gibi işlemler için el ile eylem yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="47329-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="47329-118">.NET Core 2,2 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="47329-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="47329-119">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="47329-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="47329-120">Kaynak URL 'ye "API/v2/Package" eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="47329-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="47329-121">.NET Core 2,1 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="47329-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="47329-122">Kullanıcı giriş veya teyitlerini istemez.</span><span class="sxs-lookup"><span data-stu-id="47329-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="47329-123">Sunucu URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47329-123">Specifies the server URL.</span></span> <span data-ttu-id="47329-124">Nuget.org için desteklenen URL 'Ler `https://www.nuget.org`, `https://www.nuget.org/api/v3`ve `https://www.nuget.org/api/v2/package`içerir.</span><span class="sxs-lookup"><span data-stu-id="47329-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="47329-125">Özel akışlar için ana bilgisayar adını (örneğin, `%hostname%/api/v3`) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="47329-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="47329-126">Örnekler</span><span class="sxs-lookup"><span data-stu-id="47329-126">Examples</span></span>

* <span data-ttu-id="47329-127">`Microsoft.AspNetCore.Mvc`paketinin 1,0 sürümünü siler:</span><span class="sxs-lookup"><span data-stu-id="47329-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="47329-128">`Microsoft.AspNetCore.Mvc`paket 1,0 sürümünü siler, kullanıcıdan kimlik bilgilerini veya diğer girişleri sorma:</span><span class="sxs-lookup"><span data-stu-id="47329-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
