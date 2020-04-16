---
title: dotnet nuget silme komutu
description: Dotnet-nuget-delete komutu bir paketi sunucudan siler veya listeler.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4fa4f24adba251d7872986de4a8b1a63203c36c3
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463579"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="392ed-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="392ed-103">dotnet nuget delete</span></span>

<span data-ttu-id="392ed-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 1.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="392ed-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="392ed-105">Adı</span><span class="sxs-lookup"><span data-stu-id="392ed-105">Name</span></span>

<span data-ttu-id="392ed-106">`dotnet nuget delete`- Bir paketi sunucudan siler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="392ed-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="392ed-107">Özet</span><span class="sxs-lookup"><span data-stu-id="392ed-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [--no-service-endpoint]
    [--non-interactive] [-s|--source <SOURCE>]

dotnet nuget delete -h|--help
```

## <a name="description"></a><span data-ttu-id="392ed-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="392ed-108">Description</span></span>

<span data-ttu-id="392ed-109">Komut, `dotnet nuget delete` bir paketi sunucudan siler veya boşaltıyor.</span><span class="sxs-lookup"><span data-stu-id="392ed-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="392ed-110">[nuget.org](https://www.nuget.org/)için, eylem paketi unlist etmektir.</span><span class="sxs-lookup"><span data-stu-id="392ed-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="392ed-111">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="392ed-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="392ed-112">Silmek için paketin adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="392ed-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="392ed-113">Paketin sürümü silinecek.</span><span class="sxs-lookup"><span data-stu-id="392ed-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="392ed-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="392ed-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="392ed-115">Uygulamayı değişmez, İngilizce tabanlı bir kültür kullanarak çalıştırmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="392ed-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="392ed-116">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="392ed-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="392ed-117">Komutun engellenmesine izin verir ve kimlik doğrulama gibi işlemler için el ile eylem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="392ed-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="392ed-118">Seçenek .NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="392ed-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="392ed-119">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="392ed-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="392ed-120">Kaynak URL'ye "api/v2/package" eklenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="392ed-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="392ed-121">Seçenek .NET Core 2.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="392ed-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="392ed-122">Kullanıcı girişi veya onayları istenmez.</span><span class="sxs-lookup"><span data-stu-id="392ed-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="392ed-123">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="392ed-123">Specifies the server URL.</span></span> <span data-ttu-id="392ed-124">nuget.org için desteklenen URL'ler `https://www.nuget.org/api/v3`, `https://www.nuget.org/api/v2/package` `https://www.nuget.org`ve .</span><span class="sxs-lookup"><span data-stu-id="392ed-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="392ed-125">Özel akışlar için ana bilgisayar adını `%hostname%/api/v3`değiştirin (örneğin, ).</span><span class="sxs-lookup"><span data-stu-id="392ed-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="392ed-126">Örnekler</span><span class="sxs-lookup"><span data-stu-id="392ed-126">Examples</span></span>

* <span data-ttu-id="392ed-127">Paketin `Microsoft.AspNetCore.Mvc`sürüm 1.0'ını siler:</span><span class="sxs-lookup"><span data-stu-id="392ed-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="392ed-128">Paketin `Microsoft.AspNetCore.Mvc`sürüm 1.0'ını siler, kullanıcıdan kimlik bilgileri veya diğer girişler için istenmez:</span><span class="sxs-lookup"><span data-stu-id="392ed-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
