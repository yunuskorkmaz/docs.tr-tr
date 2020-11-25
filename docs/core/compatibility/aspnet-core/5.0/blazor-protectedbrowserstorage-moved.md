---
title: 'Son değişiklik: Blazor: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c8058adf8b66aef8dd011ea672cd306ae4de60a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761478"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="22f28-103">Blazor: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı</span><span class="sxs-lookup"><span data-stu-id="22f28-103">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="22f28-104">ASP.NET Core 5,0 RC2 sürümünün bir parçası olarak, `ProtectedBrowserStorage` özellik ASP.NET Core paylaşılan çerçeveye taşınır.</span><span class="sxs-lookup"><span data-stu-id="22f28-104">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="22f28-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="22f28-105">Version introduced</span></span>

<span data-ttu-id="22f28-106">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="22f28-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="22f28-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="22f28-107">Old behavior</span></span>

<span data-ttu-id="22f28-108">ASP.NET Core 5,0 Preview 8 ' de, özelliği [Microsoft. AspNetCore. components. Web. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) paketinin bir parçası olarak kullanılabilir ancak yalnızca Blazor WebAssembly ' de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="22f28-108">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="22f28-109">ASP.NET Core 5,0 RC1 sürümünde, özelliği paylaşılan çerçeveye başvuran [Microsoft. AspNetCore. components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) paketinin bir parçası olarak kullanılabilir `Microsoft.AspNetCore.App` .</span><span class="sxs-lookup"><span data-stu-id="22f28-109">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="22f28-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="22f28-110">New behavior</span></span>

<span data-ttu-id="22f28-111">ASP.NET Core 5,0 RC2 'de, artık bu özelliği kullanmak için bir NuGet paket başvurusuna gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="22f28-111">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="22f28-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="22f28-112">Reason for change</span></span>

<span data-ttu-id="22f28-113">Paylaşılan çerçeveye taşıma, müşterilerin beklediği Kullanıcı deneyimi için daha iyi bir uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="22f28-113">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="22f28-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="22f28-114">Recommended action</span></span>

<span data-ttu-id="22f28-115">ASP.NET Core 5,0 RC1 'den yükseltme yapıyorsanız, aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="22f28-115">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="22f28-116">`Microsoft.AspNetCore.Components.ProtectedBrowserStorage`Paket başvurusunu projeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="22f28-116">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="22f28-117">`using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.</span><span class="sxs-lookup"><span data-stu-id="22f28-117">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="22f28-118">Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .</span><span class="sxs-lookup"><span data-stu-id="22f28-118">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="22f28-119">ASP.NET Core 5,0 Preview 8 ' den yükseltiyorsanız aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="22f28-119">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="22f28-120">`Microsoft.AspNetCore.Components.Web.Extensions`Paket başvurusunu projeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="22f28-120">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="22f28-121">`using Microsoft.AspNetCore.Components.Web.Extensions;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.</span><span class="sxs-lookup"><span data-stu-id="22f28-121">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="22f28-122">Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .</span><span class="sxs-lookup"><span data-stu-id="22f28-122">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="22f28-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="22f28-123">Affected APIs</span></span>

<span data-ttu-id="22f28-124">Yok</span><span class="sxs-lookup"><span data-stu-id="22f28-124">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
