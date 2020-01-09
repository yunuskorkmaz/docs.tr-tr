---
title: Xamarin sınırlamaları
ms.date: 12/13/2019
description: Xamarin kullanırken karşılaştığınız kısıtlamaların bazılarını açıklar.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447169"
---
# <a name="xamarin-limitations"></a><span data-ttu-id="67b53-103">Xamarin sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="67b53-103">Xamarin limitations</span></span>

<span data-ttu-id="67b53-104">Microsoft. Data. SQLite, 2,0 .NET Standard hedefler ve Xamarin 'te desteklenir.</span><span class="sxs-lookup"><span data-stu-id="67b53-104">Microsoft.Data.Sqlite targets .NET Standard 2.0 and is supported on Xamarin.</span></span> <span data-ttu-id="67b53-105">Aşağıdaki tabloda, varsayılan SQLitePCLRaw paketinin, için yerel SQLite ikililerini sağladığı platformlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67b53-105">The following table shows which platforms the default SQLitePCLRaw bundle provides native SQLite binaries for.</span></span> <span data-ttu-id="67b53-106">Farklı bir paket kullanma veya kendi yerel SQLite ikililerini sağlama hakkındaki ayrıntılar için bkz. [özel SQLite sürümleri](custom-versions.md) .</span><span class="sxs-lookup"><span data-stu-id="67b53-106">See [Custom SQLite versions](custom-versions.md) for details on using a different bundle or providing your own native SQLite binaries.</span></span>

| <span data-ttu-id="67b53-107">Platform</span><span class="sxs-lookup"><span data-stu-id="67b53-107">Platform</span></span> | <span data-ttu-id="67b53-108">SQLite ikililer</span><span class="sxs-lookup"><span data-stu-id="67b53-108">SQLite binaries</span></span> |
| --- | --- |
| <span data-ttu-id="67b53-109">**Xamarin.Android**</span><span class="sxs-lookup"><span data-stu-id="67b53-109">**Xamarin.Android**</span></span> | <span data-ttu-id="67b53-110">—</span><span class="sxs-lookup"><span data-stu-id="67b53-110">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | <span data-ttu-id="67b53-111">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-111">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | <span data-ttu-id="67b53-112">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-112">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="67b53-113">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-113">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | <span data-ttu-id="67b53-114">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-114">✔</span></span> |
| <span data-ttu-id="67b53-115">**Xamarin.iOS**</span><span class="sxs-lookup"><span data-stu-id="67b53-115">**Xamarin.iOS**</span></span> | <span data-ttu-id="67b53-116">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-116">✔</span></span> |
| <span data-ttu-id="67b53-117">**Xamarin.Mac**</span><span class="sxs-lookup"><span data-stu-id="67b53-117">**Xamarin.Mac**</span></span> | <span data-ttu-id="67b53-118">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-118">✔</span></span> |
| <span data-ttu-id="67b53-119">**Xamarin. TVOS**</span><span class="sxs-lookup"><span data-stu-id="67b53-119">**Xamarin.TVOS**</span></span> | <span data-ttu-id="67b53-120">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-120">✔</span></span> |
| <span data-ttu-id="67b53-121">**UWP**</span><span class="sxs-lookup"><span data-stu-id="67b53-121">**UWP**</span></span> | <span data-ttu-id="67b53-122">—</span><span class="sxs-lookup"><span data-stu-id="67b53-122">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | <span data-ttu-id="67b53-123">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-123">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | <span data-ttu-id="67b53-124">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-124">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | <span data-ttu-id="67b53-125">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-125">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="67b53-126">✔</span><span class="sxs-lookup"><span data-stu-id="67b53-126">✔</span></span> |

## <a name="ios"></a><span data-ttu-id="67b53-127">iOS</span><span class="sxs-lookup"><span data-stu-id="67b53-127">iOS</span></span>

<span data-ttu-id="67b53-128">Microsoft. Data. SQLite, SQLitePCLRaw paketlerini otomatik olarak başlatmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="67b53-128">Microsoft.Data.Sqlite tries to automatically initialize SQLitePCLRaw bundles.</span></span> <span data-ttu-id="67b53-129">Ne yazık ki, Xamarin. iOS için sonraki zaman (AOT) derlemesinde sınırlamalar nedeniyle, deneme başarısız olur ve aşağıdaki hatayı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="67b53-129">Unfortunately, because of limitations in the ahead-of-time (AOT) compilation for Xamarin.iOS, the attempt fails and you get the following error.</span></span>

> <span data-ttu-id="67b53-130">`SQLitePCL.raw.SetProvider()`çağırmanız gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="67b53-130">You need to call `SQLitePCL.raw.SetProvider()`.</span></span> <span data-ttu-id="67b53-131">Paket paketi kullanıyorsanız, bu, `SQLitePCL.Batteries.Init()`çağırarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="67b53-131">If you're using a bundle package, this is done by calling `SQLitePCL.Batteries.Init()`.</span></span>

<span data-ttu-id="67b53-132">Paketi başlatmak için, Microsoft. Data. SQLite kullanılmadan önce aşağıdaki kod satırını uygulamanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67b53-132">To initialize the bundle, add the following line of code to your app before using Microsoft.Data.Sqlite.</span></span>

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a><span data-ttu-id="67b53-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67b53-133">See also</span></span>

* [<span data-ttu-id="67b53-134">Zaman uyumsuz sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="67b53-134">Async limitations</span></span>](async.md)
* [<span data-ttu-id="67b53-135">Özel SQLite sürümleri</span><span class="sxs-lookup"><span data-stu-id="67b53-135">Custom SQLite versions</span></span>](custom-versions.md)
