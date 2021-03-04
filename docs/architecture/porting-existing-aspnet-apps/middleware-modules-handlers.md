---
title: Ara yazılımı modüller ve işleyicilerle karşılaştırın
description: Bu bölüm, istek işleme ardışık düzenleri için ara yazılımı tanımlayan ASP.NET Core uygulamalarla işleyicileri ve modülleri kullanan ASP.NET uygulamaları için yapı farklarını ele alırlar.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 040ae49d1307ef4dcc9dbf49b20544e9cd2bc913
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105903"
---
# <a name="compare-middleware-to-modules-and-handlers"></a><span data-ttu-id="dbfd6-103">Ara yazılımı modüller ve işleyicilerle karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="dbfd6-103">Compare middleware to modules and handlers</span></span>

<span data-ttu-id="dbfd6-104">Mevcut ASP.NET MVC veya Web API uygulamanız OWıN/Katana kullanıyorsa, en büyük olasılıkla ara yazılım kavramı hakkında bilgi sahibi olduğunuz ASP.NET Core oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-104">If your existing ASP.NET MVC or Web API app uses OWIN/Katana, you're most likely already familiar with the concept of middleware and porting it to ASP.NET Core should be fairly straightforward.</span></span> <span data-ttu-id="dbfd6-105">Ancak, çoğu ASP.NET uygulaması, ara yazılım yerine HTTP modüllerine ve HTTP işleyicileriyle yararlanır.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-105">However, most ASP.NET apps rely on HTTP modules and HTTP handlers instead of middleware.</span></span> <span data-ttu-id="dbfd6-106">Bunları ASP.NET Core geçirmek için ek çaba gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-106">Migrating these to ASP.NET Core requires extra effort.</span></span>

## <a name="aspnet-modules-and-handlers"></a><span data-ttu-id="dbfd6-107">ASP.NET modülleri ve işleyicileri</span><span class="sxs-lookup"><span data-stu-id="dbfd6-107">ASP.NET modules and handlers</span></span>

<span data-ttu-id="dbfd6-108">[Http modülleri ve http işleyicileri](/troubleshoot/aspnet/http-modules-handlers) , ASP.NET mimarisinin ayrılmaz bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-108">[HTTP modules and HTTP handlers](/troubleshoot/aspnet/http-modules-handlers) are an integral part of the ASP.NET architecture.</span></span> <span data-ttu-id="dbfd6-109">İstek işlenirken, her istek birden çok HTTP modülü tarafından işlenir (örneğin, kimlik doğrulama modülü ve oturum modülü) ve ardından tek bir HTTP işleyici tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-109">While a request is being processed, each request is processed by multiple HTTP modules (for example, the authentication module and the session module) and is then processed by a single HTTP handler.</span></span> <span data-ttu-id="dbfd6-110">İşleyici isteği işledikten sonra, istek HTTP modülleri üzerinden geri akar.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-110">After the handler has processed the request, the request flows back through the HTTP modules.</span></span>

<span data-ttu-id="dbfd6-111">Uygulamanız özel HTTP modülleri veya HTTP işleyicileri kullanıyorsa, bunları ASP.NET Core geçirme planına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-111">If your app is using custom HTTP modules or HTTP handlers, you'll need a plan to migrate them to ASP.NET Core.</span></span> <span data-ttu-id="dbfd6-112">ASP.NET Core en olası değişikliği ara yazılımlar.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-112">The most likely replacement in ASP.NET Core is middleware.</span></span>

## <a name="aspnet-core-middleware"></a><span data-ttu-id="dbfd6-113">ASP.NET Core ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="dbfd6-113">ASP.NET Core middleware</span></span>

<span data-ttu-id="dbfd6-114">ASP.NET Core her uygulamanın yönteminde bir istek işlem hattı tanımlar `Configure` .</span><span class="sxs-lookup"><span data-stu-id="dbfd6-114">ASP.NET Core defines a request pipeline in each app's `Configure` method.</span></span> <span data-ttu-id="dbfd6-115">Bu istek ardışık düzeni, bir gelen isteğin uygulama tarafından nasıl işlendiğini tanımlar. işlem hattının her bir yöntemi, bir yöntem sonlanana kadar bir sonraki yöntemi çağırır ve *Ara yazılım* zinciri sonlandırıldığında ve yığın geri döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-115">This request pipeline defines how an incoming request is handled by the app, with each method in the pipeline calling the next method until eventually a method terminates, and the chain of *middleware* terminates and returns back up the stack.</span></span> <span data-ttu-id="dbfd6-116">Ara yazılım tüm istekleri hedefleyebilir veya yalnızca istenen yola veya diğer faktörlere bağlı olarak belirli isteklere eşlenecek şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-116">Middleware can target all requests, or can be configured to only map to certain requests based on the requested path or other factors.</span></span> <span data-ttu-id="dbfd6-117">`Configure`Uygulama yönteminde tamamen veya ayrı bir sınıfta uygulanan şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-117">It can be configured wholly in the `Configure` method of an app, or implemented in a separate class.</span></span>

<span data-ttu-id="dbfd6-118">HTTP modüllerini kullanan bir ASP.NET MVC uygulamasındaki davranış, büyük olasılıkla [özel ara yazılım](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)için en uygun seçenektir.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-118">Behavior in an ASP.NET MVC app that uses HTTP modules is probably best suited to [custom middleware](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span></span> <span data-ttu-id="dbfd6-119">Özel HTTP işleyicileri, aynı yola yanıt veren özel rotalar veya uç noktalar ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="dbfd6-119">Custom HTTP handlers can be replaced with custom routes or endpoints that respond to the same path.</span></span>

## <a name="references"></a><span data-ttu-id="dbfd6-120">Başvurular</span><span class="sxs-lookup"><span data-stu-id="dbfd6-120">References</span></span>

- [<span data-ttu-id="dbfd6-121">ASP.NET HTTP modülleri ve HTTP işleyicileri</span><span class="sxs-lookup"><span data-stu-id="dbfd6-121">ASP.NET HTTP modules and HTTP handlers</span></span>](/troubleshoot/aspnet/http-modules-handlers)
- [<span data-ttu-id="dbfd6-122">ASP.NET Core ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="dbfd6-122">ASP.NET Core middleware</span></span>](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
><span data-ttu-id="dbfd6-123">[Önceki](dependency-injection-differences.md) 
> [Sonraki](configuration-differences.md)</span><span class="sxs-lookup"><span data-stu-id="dbfd6-123">[Previous](dependency-injection-differences.md)
[Next](configuration-differences.md)</span></span>
