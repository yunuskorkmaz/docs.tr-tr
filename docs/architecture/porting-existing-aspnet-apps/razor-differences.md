---
title: ASP.NET MVC ve ASP.NET Core Razor kullanımını karşılaştırın
description: ASP.NET MVC ve ASP.NET Core arasında Razor farklı midir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 355506364e32283cb86bd21b82d7de672a974829
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488952"
---
# <a name="compare-razor-usage-in-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="b80f4-103">ASP.NET MVC ve ASP.NET Core Razor kullanımını karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="b80f4-103">Compare Razor usage in ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="b80f4-104">Razor 'nin temel sözdizimi, ASP.NET MVC ve ASP.NET Core arasında önemli ölçüde değişmemiştir.</span><span class="sxs-lookup"><span data-stu-id="b80f4-104">The basic syntax of Razor hasn't changed substantially between ASP.NET MVC and ASP.NET Core.</span></span> <span data-ttu-id="b80f4-105">Ancak, geçiş sırasında göz önünde bulundurmanız gereken [Etiket Yardımcıları](https://docs.microsoft.com/aspnet/core/mvc/views/tag-helpers/intro) ve Razor Pages giriş gibi bazı farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="b80f4-105">However, there are certain differences, such as the introduction of [Tag Helpers](https://docs.microsoft.com/aspnet/core/mvc/views/tag-helpers/intro) and Razor Pages, that should be considered when migrating.</span></span> <span data-ttu-id="b80f4-106">Uygulamanız özel Razor işlevlerinin ağır kullanımını yapıyorsa, ASP.NET Core 'e geçiş yaparken hangi değişikliklerin gerekli olabileceğini görmek için [ASP.NET Core Razor söz dizimi başvurusuna](https://docs.microsoft.com/aspnet/core/razor-pages) bakın.</span><span class="sxs-lookup"><span data-stu-id="b80f4-106">If your app makes heavy use of custom Razor functionality, refer to the [Razor syntax reference for ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages) to see what changes may be required when you migrate to ASP.NET Core.</span></span>

## <a name="tag-helpers"></a><span data-ttu-id="b80f4-107">Etiket Yardımcıları</span><span class="sxs-lookup"><span data-stu-id="b80f4-107">Tag Helpers</span></span>

<span data-ttu-id="b80f4-108">Etiket Yardımcıları, Razor dosyalarında HTML öğelerinin oluşturulmasına ve işlenmesine sunucu tarafı kodun katılmasını etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="b80f4-108">Tag Helpers enable server-side code to participate in creating and rendering HTML elements in Razor files.</span></span> <span data-ttu-id="b80f4-109">Bunlar HTML yardımcılarına göre birçok avantaj sunar ve mümkün olan yerlerde HTML yardımcılarının yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b80f4-109">They offer many advantages over HTML Helpers and should be used in place of HTML Helpers wherever possible.</span></span> <span data-ttu-id="b80f4-110">Bunlar standart HTML gibi göründiklerinden ve HTML düzenlemek için tasarlanan çoğu araç tarafından yoksayıldığından, HTML kullanımı kolay bir geliştirme deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b80f4-110">They provide an HTML-friendly development experience, since they look like standard HTML and are ignored by most tooling designed to edit HTML.</span></span> <span data-ttu-id="b80f4-111">_Visual Studio_'Da, etiket YARDıMCıLARı ile HTML ve Razor biçimlendirmesi oluşturmaya yönelik zengin IntelliSense desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="b80f4-111">Within _Visual Studio_, there's rich IntelliSense support for creating HTML and Razor markup with Tag Helpers.</span></span> <span data-ttu-id="b80f4-112">Etiket Yardımcıları, Razor dosyalarındaki bildirime dayalı biçimlendirmeden basit veya karmaşık davranış sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b80f4-112">Tag Helpers can provide simple or complex behavior from declarative markup in Razor files.</span></span>

## <a name="razor-pages"></a><span data-ttu-id="b80f4-113">Razor Pages</span><span class="sxs-lookup"><span data-stu-id="b80f4-113">Razor Pages</span></span>

<span data-ttu-id="b80f4-114">Razor Pages, sayfa ve form tabanlı uygulamalara yönelik denetleyiciler, Eylemler ve görünümlere bir alternatif sunar.</span><span class="sxs-lookup"><span data-stu-id="b80f4-114">Razor Pages offer an alternative to controllers, actions, and views for page- and form-based apps.</span></span> <span data-ttu-id="b80f4-115">[Razor Pages, bu bölümde daha önce ASP.NET MVC ile karşılaştırıldı](./comparing-razor-pages-aspnet-mvc.md).</span><span class="sxs-lookup"><span data-stu-id="b80f4-115">[Razor Pages were compared to ASP.NET MVC earlier in this chapter](./comparing-razor-pages-aspnet-mvc.md).</span></span>

## <a name="references"></a><span data-ttu-id="b80f4-116">Başvurular</span><span class="sxs-lookup"><span data-stu-id="b80f4-116">References</span></span>

- [<span data-ttu-id="b80f4-117">ASP.NET MVC 'den ASP.NET Core MVC: denetleyiciler ve görünümler 'e geçiş</span><span class="sxs-lookup"><span data-stu-id="b80f4-117">Migrate from ASP.NET MVC to ASP.NET Core MVC: Controllers and Views</span></span>](https://docs.microsoft.com/aspnet/core/migration/mvc#migrate-controllers-and-views)
- [<span data-ttu-id="b80f4-118">ASP.NET Core etiket yardımcıları</span><span class="sxs-lookup"><span data-stu-id="b80f4-118">Tag Helpers in ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/mvc/views/tag-helpers/intro)
- [<span data-ttu-id="b80f4-119">ASP.NET Core Razor Pages giriş</span><span class="sxs-lookup"><span data-stu-id="b80f4-119">Introduction to Razor Pages in ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/razor-pages)
- [<span data-ttu-id="b80f4-120">ASP.NET Core için Razor söz dizimi başvurusu</span><span class="sxs-lookup"><span data-stu-id="b80f4-120">Razor syntax reference for ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/razor-pages)

>[!div class="step-by-step"]
><span data-ttu-id="b80f4-121">[Önceki](controller-differences.md) 
> [Sonraki](signalr-differences.md)</span><span class="sxs-lookup"><span data-stu-id="b80f4-121">[Previous](controller-differences.md)
[Next](signalr-differences.md)</span></span>
