---
title: ASP.NET MVC ve ASP.NET Core arasındaki barındırma farklılıkları
description: ASP.NET MVC uygulamalarının ASP.NET Core uygulamalara karşı nasıl barındırıldığı ile arasındaki farklılıklara genel bakış.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 402dd5782cb215545ff2ef13f97ec269b8a2540b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106021"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="7c73e-103">ASP.NET MVC ve ASP.NET Core arasındaki barındırma farklılıkları</span><span class="sxs-lookup"><span data-stu-id="7c73e-103">Hosting differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="7c73e-104">ASP.NET MVC uygulamaları IIS 'de barındırılır ve davranışları için IIS yapılandırmasına bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c73e-104">ASP.NET MVC apps are hosted in IIS, and may rely on IIS configuration for their behavior.</span></span> <span data-ttu-id="7c73e-105">Bu genellikle [IIS modüllerini](/iis/get-started/introduction-to-iis/iis-modules-overview)içerir.</span><span class="sxs-lookup"><span data-stu-id="7c73e-105">This often includes [IIS modules](/iis/get-started/introduction-to-iis/iis-modules-overview).</span></span> <span data-ttu-id="7c73e-106">ASP.NET MVC 'den ASP.NET Core 'e bağlantı noktasına hazırlanmaya yönelik bir uygulama gözden geçirilme kapsamında, takımlar, varsa, sunucusunda yüklü olan IIS modülleri listesinden hangi modüllerin kullandığını tanımlarlar.</span><span class="sxs-lookup"><span data-stu-id="7c73e-106">As part of reviewing an app to prepare to port it from ASP.NET MVC to ASP.NET Core, teams should identify which modules, if any, they're using from the list of IIS Modules installed on their server.</span></span>

<span data-ttu-id="7c73e-107">[ASP.NET Core uygulamalar birçok farklı sunucu üzerinde çalışabilir](/aspnet/core/fundamentals/servers/).</span><span class="sxs-lookup"><span data-stu-id="7c73e-107">[ASP.NET Core apps can run on a number of different servers](/aspnet/core/fundamentals/servers/).</span></span> <span data-ttu-id="7c73e-108">Varsayılan Kestrel platformlar arası sunucu, iyi bir varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="7c73e-108">The default cross platform server, Kestrel, is a good default choice.</span></span> <span data-ttu-id="7c73e-109">Kestrel ' de çalışan uygulamalar IIS tarafından barındırılabilir ve ayrı bir işlemde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c73e-109">Apps running in Kestrel can be hosted by IIS, running in a separate process.</span></span> <span data-ttu-id="7c73e-110">Windows 'da, uygulamalar IIS 'de veya HTTP.sys kullanarak da çalışır.</span><span class="sxs-lookup"><span data-stu-id="7c73e-110">On Windows, apps can also run in process on IIS or using HTTP.sys.</span></span> <span data-ttu-id="7c73e-111">Kestrel genellikle en iyi performans için önerilir.</span><span class="sxs-lookup"><span data-stu-id="7c73e-111">Kestrel is generally recommended for best performance.</span></span> <span data-ttu-id="7c73e-112">HTTP.sys, uygulamanın Internet 'e sunulabileceği senaryolarda ve gerekli yetenekler, HTTP.sys tarafından desteklenmediği durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c73e-112">HTTP.sys can be used in scenarios where the app is exposed to the Internet and required capabilities are supported by HTTP.sys but not Kestrel.</span></span>

<span data-ttu-id="7c73e-113">Kestrel, IIS modülleriyle eşdeğer değildir (ancak IIS 'de barındırılan uygulamalar IIS modüllerinden yine de faydalanabilir).</span><span class="sxs-lookup"><span data-stu-id="7c73e-113">Kestrel does not have an equivalent to IIS modules (though apps hosted in IIS can still take advantage of IIS modules).</span></span> <span data-ttu-id="7c73e-114">Eşdeğer davranış elde etmek için, ASP.NET Core uygulamada yapılandırılan ara yazılım genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c73e-114">To achieve equivalent behavior, middleware configured in the ASP.NET Core app itself is typically used.</span></span>

## <a name="references"></a><span data-ttu-id="7c73e-115">Başvurular</span><span class="sxs-lookup"><span data-stu-id="7c73e-115">References</span></span>

- [<span data-ttu-id="7c73e-116">IIS Modülleri</span><span class="sxs-lookup"><span data-stu-id="7c73e-116">IIS Modules</span></span>](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [<span data-ttu-id="7c73e-117">ASP.NET Core sunucuları</span><span class="sxs-lookup"><span data-stu-id="7c73e-117">ASP.NET Core Servers</span></span>](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
><span data-ttu-id="7c73e-118">[Önceki](app-startup-differences.md) 
> [Sonraki](serving-static-files.md)</span><span class="sxs-lookup"><span data-stu-id="7c73e-118">[Previous](app-startup-differences.md)
[Next](serving-static-files.md)</span></span>
