---
title: ASP.NET MVC ve ASP.NET Core arasındaki mimari farklar
description: ASP.NET ve ASP.NET Core arasındaki mimari farklılıkları inceleyin.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0e546465a3da6971a118c65114af81c3a387e00e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488926"
---
# <a name="architectural-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="23189-103">ASP.NET MVC ve ASP.NET Core arasındaki mimari farklar</span><span class="sxs-lookup"><span data-stu-id="23189-103">Architectural differences between ASP.NET MVC and ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="23189-104">.NET Framework ve ASP.NET Core üzerinde ASP.NET MVC arasında birçok mimari fark vardır.</span><span class="sxs-lookup"><span data-stu-id="23189-104">There are many architectural differences between ASP.NET MVC on .NET Framework and ASP.NET Core.</span></span> <span data-ttu-id="23189-105">Takımlar, ASP.NET MVC uygulamalarını ASP.NET Core 'e taşıma konusunda yer alan işi değerlendirirken, bu farklılıkları büyük bir şekilde kavramak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="23189-105">It's important to have a broad understanding of these differences as teams evaluate the work involved in porting their ASP.NET MVC apps to ASP.NET Core.</span></span> <span data-ttu-id="23189-106">Bu bölümde, ASP.NET Core ASP.NET MVC 'den önemli ölçüde farklı olan her bir yol görünür.</span><span class="sxs-lookup"><span data-stu-id="23189-106">This chapter looks at each of the ways in which ASP.NET Core differs substantially from ASP.NET MVC.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="23189-107">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="23189-107">Breaking changes</span></span>

<span data-ttu-id="23189-108">.NET Core, .NET Framework platformlar arası yeniden yazma işlemi.</span><span class="sxs-lookup"><span data-stu-id="23189-108">.NET Core is a cross-platform rewrite of .NET Framework.</span></span> <span data-ttu-id="23189-109">[İki çerçeve arasında çok sayıda Son değişiklik](https://docs.microsoft.com/dotnet/core/compatibility/fx-core)vardır.</span><span class="sxs-lookup"><span data-stu-id="23189-109">There are many [breaking changes between the two frameworks](https://docs.microsoft.com/dotnet/core/compatibility/fx-core).</span></span> <span data-ttu-id="23189-110">Aşağıdaki bölümler, ASP.NET MVC ve ASP.NET Core uygulamalarının nasıl tasarlandığına ve geliştirildiğiyle ilgili belirli farklılıkları belirler.</span><span class="sxs-lookup"><span data-stu-id="23189-110">The following sections identify specific differences between how ASP.NET MVC and ASP.NET Core apps are designed and developed.</span></span> <span data-ttu-id="23189-111">Ayrıca, hangi çerçeve kitaplıklarının değişiklik yapması gerektiğini belirleyen belgeleri incelemek için de dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="23189-111">Take care to also examine the documentation to determine which framework libraries you're using that may need to change.</span></span> <span data-ttu-id="23189-112">Birçok durumda, bir değiştirme NuGet paketi .NET Framework ve .NET Core arasında kalan boşlukları dolduracak şekilde bulunur.</span><span class="sxs-lookup"><span data-stu-id="23189-112">In many cases, a replacement NuGet package exists to fill in any gaps left between .NET Framework and .NET Core.</span></span> <span data-ttu-id="23189-113">Nadir durumlarda, uyumsuzlukları karşılamak için bir üçüncü taraf çözümü bulmanız veya yeni özel kod uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="23189-113">In rare cases, you may need to find a third-party solution or implement new custom code to address incompatibilities.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="23189-114">[Önceki](additional-migration-resources.md) 
> [Sonraki](app-startup-differences.md)</span><span class="sxs-lookup"><span data-stu-id="23189-114">[Previous](additional-migration-resources.md)
[Next](app-startup-differences.md)</span></span>
