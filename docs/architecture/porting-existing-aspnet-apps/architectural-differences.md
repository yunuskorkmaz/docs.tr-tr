---
title: ASP.NET MVC ve ASP.NET Core arasındaki mimari farklar
description: ASP.NET ve ASP.NET Core arasındaki mimari farklılıkları inceleyin.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 96477f2393482380eee9891e9b2dbbb6445e15bd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106153"
---
# <a name="architectural-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="73d2f-103">ASP.NET MVC ve ASP.NET Core arasındaki mimari farklar</span><span class="sxs-lookup"><span data-stu-id="73d2f-103">Architectural differences between ASP.NET MVC and ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="73d2f-104">.NET Framework ve ASP.NET Core üzerinde ASP.NET MVC arasında birçok mimari fark vardır.</span><span class="sxs-lookup"><span data-stu-id="73d2f-104">There are many architectural differences between ASP.NET MVC on .NET Framework and ASP.NET Core.</span></span> <span data-ttu-id="73d2f-105">Takımlar, ASP.NET MVC uygulamalarını ASP.NET Core 'e taşıma konusunda yer alan işi değerlendirirken, bu farklılıkları büyük bir şekilde kavramak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="73d2f-105">It's important to have a broad understanding of these differences as teams evaluate the work involved in porting their ASP.NET MVC apps to ASP.NET Core.</span></span> <span data-ttu-id="73d2f-106">Bu bölümde, ASP.NET Core ASP.NET MVC 'den önemli ölçüde farklı olan her bir yol görünür.</span><span class="sxs-lookup"><span data-stu-id="73d2f-106">This chapter looks at each of the ways in which ASP.NET Core differs substantially from ASP.NET MVC.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="73d2f-107">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="73d2f-107">Breaking changes</span></span>

<span data-ttu-id="73d2f-108">.NET Core, .NET Framework platformlar arası yeniden yazma işlemi.</span><span class="sxs-lookup"><span data-stu-id="73d2f-108">.NET Core is a cross-platform rewrite of .NET Framework.</span></span> <span data-ttu-id="73d2f-109">[İki çerçeve arasında çok sayıda Son değişiklik](../../core/compatibility/fx-core.md)vardır.</span><span class="sxs-lookup"><span data-stu-id="73d2f-109">There are many [breaking changes between the two frameworks](../../core/compatibility/fx-core.md).</span></span> <span data-ttu-id="73d2f-110">Aşağıdaki bölümler, ASP.NET MVC ve ASP.NET Core uygulamalarının nasıl tasarlandığına ve geliştirildiğiyle ilgili belirli farklılıkları belirler.</span><span class="sxs-lookup"><span data-stu-id="73d2f-110">The following sections identify specific differences between how ASP.NET MVC and ASP.NET Core apps are designed and developed.</span></span> <span data-ttu-id="73d2f-111">Ayrıca, hangi çerçeve kitaplıklarının değişiklik yapması gerektiğini belirleyen belgeleri incelemek için de dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73d2f-111">Take care to also examine the documentation to determine which framework libraries you're using that may need to change.</span></span> <span data-ttu-id="73d2f-112">Birçok durumda, bir değiştirme NuGet paketi .NET Framework ve .NET Core arasında kalan boşlukları dolduracak şekilde bulunur.</span><span class="sxs-lookup"><span data-stu-id="73d2f-112">In many cases, a replacement NuGet package exists to fill in any gaps left between .NET Framework and .NET Core.</span></span> <span data-ttu-id="73d2f-113">Nadir durumlarda, uyumsuzlukları karşılamak için bir üçüncü taraf çözümü bulmanız veya yeni özel kod uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="73d2f-113">In rare cases, you may need to find a third-party solution or implement new custom code to address incompatibilities.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="73d2f-114">[Önceki](additional-migration-resources.md) 
> [Sonraki](app-startup-differences.md)</span><span class="sxs-lookup"><span data-stu-id="73d2f-114">[Previous](additional-migration-resources.md)
[Next](app-startup-differences.md)</span></span>
