---
title: Modüller, işleyiciler ve ara yazılım
description: Modüller, işleyiciler ve ara yazılım ile HTTP isteklerini işleme hakkında bilgi edinin.
author: danroth27
ms.author: daroth
ms.date: 10/11/2019
ms.openlocfilehash: 3ecc109c54f88b5b06a1474f7c6e262d426a78a9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337471"
---
# <a name="modules-handlers-and-middleware"></a><span data-ttu-id="546e0-103">Modüller, işleyiciler ve ara yazılım</span><span class="sxs-lookup"><span data-stu-id="546e0-103">Modules, handlers, and middleware</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="546e0-104">ASP.NET Core bir uygulama, bir dizi *Ara yazılım*üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="546e0-104">An ASP.NET Core app is built upon a series of *middleware*.</span></span> <span data-ttu-id="546e0-105">Ara yazılım, istekleri ve yanıtları işlemek için bir işlem hattına düzenlenmiş işleyicileridir.</span><span class="sxs-lookup"><span data-stu-id="546e0-105">Middleware is handlers that are arranged into a pipeline to handle requests and responses.</span></span> <span data-ttu-id="546e0-106">Web Forms uygulamasında HTTP işleyicileri ve modülleri benzer sorunları çözecektir.</span><span class="sxs-lookup"><span data-stu-id="546e0-106">In a Web Forms app, HTTP handlers and modules solve similar problems.</span></span> <span data-ttu-id="546e0-107">ASP.NET Core, modüller, işleyiciler, *Global.asax.cs*ve uygulama yaşam döngüsü, ara yazılım ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="546e0-107">In ASP.NET Core, modules, handlers, *Global.asax.cs*, and the app life cycle are replaced with middleware.</span></span> <span data-ttu-id="546e0-108">Bu bölümde, bir Blazor uygulaması bağlamında hangi ara yazılımı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="546e0-108">In this chapter, you'll learn what middleware in the context of a Blazor app.</span></span>

## <a name="overview"></a><span data-ttu-id="546e0-109">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="546e0-109">Overview</span></span>

<span data-ttu-id="546e0-110">ASP.NET Core isteği ardışık düzeni, bir dizi istekten oluşur ve bunlardan sonra çağırılır.</span><span class="sxs-lookup"><span data-stu-id="546e0-110">The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other.</span></span> <span data-ttu-id="546e0-111">Aşağıdaki diyagramda kavram gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="546e0-111">The following diagram demonstrates the concept.</span></span> <span data-ttu-id="546e0-112">Yürütmenin iş parçacığı siyah okları izler.</span><span class="sxs-lookup"><span data-stu-id="546e0-112">The thread of execution follows the black arrows.</span></span>

![konfigüre](media/middleware/request-delegate-pipeline.png)

<span data-ttu-id="546e0-114">Önceki diyagramda yaşam döngüsü olaylarının bir kavramı yoktur.</span><span class="sxs-lookup"><span data-stu-id="546e0-114">The preceding diagram lacks a concept of lifecycle events.</span></span> <span data-ttu-id="546e0-115">Bu kavram, ASP.NET Web Forms isteklerinin nasıl işlendiği konusunda temel bir deneyimdir.</span><span class="sxs-lookup"><span data-stu-id="546e0-115">This concept is foundational to how ASP.NET Web Forms requests are handled.</span></span> <span data-ttu-id="546e0-116">Bu sistem, hangi işlemin gerçekleşmekte olduğunu ve ara yazılımın herhangi bir noktaya eklenmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="546e0-116">This system makes it easier to reason about what process is occurring and allows middleware to be inserted at any point.</span></span> <span data-ttu-id="546e0-117">Ara yazılım, istek ardışık düzenine eklendiği sırayla yürütülür.</span><span class="sxs-lookup"><span data-stu-id="546e0-117">Middleware executes in the order in which it's added to the request pipeline.</span></span> <span data-ttu-id="546e0-118">Bunlar, genellikle *Startup.cs*içinde yapılandırma dosyaları yerine kodda de eklenirler.</span><span class="sxs-lookup"><span data-stu-id="546e0-118">They're also added in code instead of configuration files, usually in *Startup.cs*.</span></span>

## <a name="katana"></a><span data-ttu-id="546e0-119">Katana</span><span class="sxs-lookup"><span data-stu-id="546e0-119">Katana</span></span>

<span data-ttu-id="546e0-120">Katana ile tanıdık okuyucular ASP.NET Core rahat bir şekilde yararlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="546e0-120">Readers familiar with Katana will feel comfortable in ASP.NET Core.</span></span> <span data-ttu-id="546e0-121">Aslında Katana, ASP.NET Core türetildiği bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="546e0-121">In fact, Katana is a framework from which ASP.NET Core derives.</span></span> <span data-ttu-id="546e0-122">ASP.NET 4. x için benzer bir ara yazılım ve ardışık düzen desenleri getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="546e0-122">It introduced similar middleware and pipeline patterns for ASP.NET 4.x.</span></span> <span data-ttu-id="546e0-123">Katana için tasarlanan ara yazılım ASP.NET Core işlem hattı ile çalışacak şekilde uyarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="546e0-123">Middleware designed for Katana can be adapted to work with the ASP.NET Core pipeline.</span></span>

## <a name="common-middleware"></a><span data-ttu-id="546e0-124">Ortak ara yazılım</span><span class="sxs-lookup"><span data-stu-id="546e0-124">Common middleware</span></span>

<span data-ttu-id="546e0-125">ASP.NET 4. x birçok modül içerir.</span><span class="sxs-lookup"><span data-stu-id="546e0-125">ASP.NET 4.x includes many modules.</span></span> <span data-ttu-id="546e0-126">Benzer bir biçimde, ASP.NET Core birçok ara yazılım bileşeni de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="546e0-126">In a similar fashion, ASP.NET Core has many middleware components available as well.</span></span> <span data-ttu-id="546e0-127">IIS modülleri, ASP.NET Core bazı durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="546e0-127">IIS modules may be used in some cases with ASP.NET Core.</span></span> <span data-ttu-id="546e0-128">Diğer durumlarda, yerel ASP.NET Core ara yazılımı kullanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="546e0-128">In other cases, native ASP.NET Core middleware may be available.</span></span>

<span data-ttu-id="546e0-129">Aşağıdaki tabloda, ASP.NET Core ' deki değiştirme ara yazılımı ve bileşenleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="546e0-129">The following table lists replacement middleware and components in ASP.NET Core.</span></span>

|<span data-ttu-id="546e0-130">Modülü</span><span class="sxs-lookup"><span data-stu-id="546e0-130">Module</span></span>                 |<span data-ttu-id="546e0-131">ASP.NET 4. x modülü</span><span class="sxs-lookup"><span data-stu-id="546e0-131">ASP.NET 4.x module</span></span>           |<span data-ttu-id="546e0-132">ASP.NET Core seçeneği</span><span class="sxs-lookup"><span data-stu-id="546e0-132">ASP.NET Core option</span></span>|
|-----------------------|-----------------------------|-------------------|
|<span data-ttu-id="546e0-133">HTTP hataları</span><span class="sxs-lookup"><span data-stu-id="546e0-133">HTTP errors</span></span>            |`CustomErrorModule`          |[<span data-ttu-id="546e0-134">Durum kodu sayfaları ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-134">Status Code Pages Middleware</span></span>](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|<span data-ttu-id="546e0-135">Varsayılan belge</span><span class="sxs-lookup"><span data-stu-id="546e0-135">Default document</span></span>       |`DefaultDocumentModule`      |[<span data-ttu-id="546e0-136">Varsayılan dosyalar ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-136">Default Files Middleware</span></span>](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|<span data-ttu-id="546e0-137">Dizin tarama</span><span class="sxs-lookup"><span data-stu-id="546e0-137">Directory browsing</span></span>     |`DirectoryListingModule`     |[<span data-ttu-id="546e0-138">Dizin tarama ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-138">Directory Browsing Middleware</span></span>](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|<span data-ttu-id="546e0-139">Dinamik sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="546e0-139">Dynamic compression</span></span>    |`DynamicCompressionModule`   |[<span data-ttu-id="546e0-140">Yanıt Sıkıştırma Ara Yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-140">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="546e0-141">Başarısız istek izleme</span><span class="sxs-lookup"><span data-stu-id="546e0-141">Failed requests tracing</span></span>|`FailedRequestsTracingModule`|[<span data-ttu-id="546e0-142">Günlüğe kaydetme ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="546e0-142">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|<span data-ttu-id="546e0-143">Dosya önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="546e0-143">File caching</span></span>           |`FileCacheModule`            |[<span data-ttu-id="546e0-144">Yanıtları Önbelleğe Alma Ara Yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-144">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="546e0-145">HTTP önbelleği</span><span class="sxs-lookup"><span data-stu-id="546e0-145">HTTP caching</span></span>           |`HttpCacheModule`            |[<span data-ttu-id="546e0-146">Yanıtları Önbelleğe Alma Ara Yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-146">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="546e0-147">HTTP günlüğü</span><span class="sxs-lookup"><span data-stu-id="546e0-147">HTTP logging</span></span>           |`HttpLoggingModule`          |[<span data-ttu-id="546e0-148">Günlüğe kaydetme ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="546e0-148">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index)|
|<span data-ttu-id="546e0-149">HTTP yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="546e0-149">HTTP redirection</span></span>       |`HttpRedirectionModule`      |[<span data-ttu-id="546e0-150">URL Yeniden Yazma Ara Yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-150">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="546e0-151">ISAPI filtreleri</span><span class="sxs-lookup"><span data-stu-id="546e0-151">ISAPI filters</span></span>          |`IsapiFilterModule`          |[<span data-ttu-id="546e0-152">Ara Yazılım</span><span class="sxs-lookup"><span data-stu-id="546e0-152">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="546e0-153">ISAPI</span><span class="sxs-lookup"><span data-stu-id="546e0-153">ISAPI</span></span>                  |`IsapiModule`                |[<span data-ttu-id="546e0-154">Ara Yazılım</span><span class="sxs-lookup"><span data-stu-id="546e0-154">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="546e0-155">İstek filtreleme</span><span class="sxs-lookup"><span data-stu-id="546e0-155">Request filtering</span></span>      |`RequestFilteringModule`     |[<span data-ttu-id="546e0-156">URL yeniden yazma ara yazılımı ırule</span><span class="sxs-lookup"><span data-stu-id="546e0-156">URL Rewriting Middleware IRule</span></span>](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|<span data-ttu-id="546e0-157">URL yeniden yazma&#8224;</span><span class="sxs-lookup"><span data-stu-id="546e0-157">URL rewriting&#8224;</span></span>   |`RewriteModule`              |[<span data-ttu-id="546e0-158">URL Yeniden Yazma Ara Yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-158">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="546e0-159">Statik sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="546e0-159">Static compression</span></span>     |`StaticCompressionModule`    |[<span data-ttu-id="546e0-160">Yanıt Sıkıştırma Ara Yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-160">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="546e0-161">Statik içerik</span><span class="sxs-lookup"><span data-stu-id="546e0-161">Static content</span></span>         |`StaticFileModule`           |[<span data-ttu-id="546e0-162">Statik dosya ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="546e0-162">Static File Middleware</span></span>](/aspnet/core/fundamentals/static-files)|
|<span data-ttu-id="546e0-163">URL yetkilendirmesi</span><span class="sxs-lookup"><span data-stu-id="546e0-163">URL authorization</span></span>      |`UrlAuthorizationModule`     |[<span data-ttu-id="546e0-164">ASP.NET Core kimliği</span><span class="sxs-lookup"><span data-stu-id="546e0-164">ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity)|

<span data-ttu-id="546e0-165">Bu liste ayrıntılı değildir ancak iki çerçeve arasında hangi eşlemenin mevcut olduğunu fikir vermelidir.</span><span class="sxs-lookup"><span data-stu-id="546e0-165">This list isn't exhaustive but should give an idea of what mapping exists between the two frameworks.</span></span> <span data-ttu-id="546e0-166">Daha ayrıntılı bir liste için bkz. [ASP.NET Core Ile IIS modülleri](/aspnet/core/host-and-deploy/iis/modules).</span><span class="sxs-lookup"><span data-stu-id="546e0-166">For a more detailed list, see [IIS modules with ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span></span>

## <a name="custom-middleware"></a><span data-ttu-id="546e0-167">Özel ara yazılım</span><span class="sxs-lookup"><span data-stu-id="546e0-167">Custom middleware</span></span>

<span data-ttu-id="546e0-168">Yerleşik ara yazılım, bir uygulama için gereken tüm senaryoları işleyemez.</span><span class="sxs-lookup"><span data-stu-id="546e0-168">Built-in middleware may not handle all scenarios needed for an app.</span></span> <span data-ttu-id="546e0-169">Böyle durumlarda, kendi ara ortamınızı oluşturmak mantıklı olur.</span><span class="sxs-lookup"><span data-stu-id="546e0-169">In such cases, it makes sense to create your own middleware.</span></span> <span data-ttu-id="546e0-170">En basit olan basit bir temsilciyle, ara yazılım tanımlamanın birden çok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="546e0-170">There are multiple ways of defining middleware, with the simplest being a simple delegate.</span></span> <span data-ttu-id="546e0-171">Bir sorgu dizesinden gelen kültür isteğini kabul eden aşağıdaki ara yazılımı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="546e0-171">Consider the following middleware, which accepts a culture request from a query string:</span></span>

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

<span data-ttu-id="546e0-172">Ara yazılım, `IMiddleware` arabirimini veya aşağıdaki ara yazılım kuralını uygulayarak da sınıf olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="546e0-172">Middleware can also be defined as class, either by implementing the `IMiddleware` interface or by following middleware convention.</span></span> <span data-ttu-id="546e0-173">Daha fazla bilgi için bkz. [özel ASP.NET Core ara yazılımı yazma](/aspnet/core/fundamentals/middleware/write).</span><span class="sxs-lookup"><span data-stu-id="546e0-173">For more information, see [Write custom ASP.NET Core middleware](/aspnet/core/fundamentals/middleware/write).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="546e0-174">[Önceki](data.md)
>[İleri](config.md)</span><span class="sxs-lookup"><span data-stu-id="546e0-174">[Previous](data.md)
[Next](config.md)</span></span>
