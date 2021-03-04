---
title: ASP.NET MVC ve ASP.NET Core arasındaki bağımlılık ekleme farkları
description: Bağımlılık ekleme 'nin ASP.NET MVC ve ASP.NET Core 'de nasıl çalıştığı, farklı oldukları ve ASP.NET MVC 'den ASP.NET Core nasıl geçirileceği hakkında bir bakış.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: aa1c7dd2f70e1a545352feb6560177bc6e2baa2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106028"
---
# <a name="dependency-injection-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="05ada-103">ASP.NET MVC ve ASP.NET Core arasındaki bağımlılık ekleme farkları</span><span class="sxs-lookup"><span data-stu-id="05ada-103">Dependency injection differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="05ada-104">Bağımlılık ekleme (DI), ASP.NET MVC veya Web API 'sine derlenmese de, birçok uygulama, denetim (ıOC) kapsayıcısının bir NuGet paketini ekleyerek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="05ada-104">Although dependency injection (DI) isn't built into ASP.NET MVC or Web API, many apps enable it by adding a NuGet package with an inversion of control (IOC) container.</span></span> <span data-ttu-id="05ada-105">Bunlar bazen bağımlılık ekleme (veya Inversion) için dı kapsayıcıları olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="05ada-105">These are sometimes referred to as DI containers, for dependency injection (or inversion).</span></span> <span data-ttu-id="05ada-106">ASP.NET MVC uygulamalarında kullanılan en popüler kapsayıcıların bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="05ada-106">Some of the most popular containers used in ASP.NET MVC apps include:</span></span>

- [<span data-ttu-id="05ada-107">Autofac</span><span class="sxs-lookup"><span data-stu-id="05ada-107">Autofac</span></span>](https://www.autofac.org/)
- [<span data-ttu-id="05ada-108">Unity</span><span class="sxs-lookup"><span data-stu-id="05ada-108">Unity</span></span>](https://unitycontainer.github.io/)
- [<span data-ttu-id="05ada-109">Nekleme</span><span class="sxs-lookup"><span data-stu-id="05ada-109">Ninject</span></span>](http://www.ninject.org/)
- <span data-ttu-id="05ada-110">[StructureMap](http://structuremap.github.io/) *(kullanım dışı)*</span><span class="sxs-lookup"><span data-stu-id="05ada-110">[StructureMap](http://structuremap.github.io/) *(deprecated)*</span></span>
- [<span data-ttu-id="05ada-111">Role Wınsörü</span><span class="sxs-lookup"><span data-stu-id="05ada-111">Castle Windsor</span></span>](http://www.castleproject.org/projects/windsor/)

<span data-ttu-id="05ada-112">ASP.NET MVC uygulamanız DI kullanıyorsa, muhtemelen ASP.NET Core için yerleşik desteğini araştırmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="05ada-112">If your ASP.NET MVC app isn't using DI, you will probably want to investigate the built-in support for DI in ASP.NET Core.</span></span> <span data-ttu-id="05ada-113">Dı, uygulamanızda gevşek modülleri yükseltir ve [katı](https://www.weeklydevtips.com/episodes/047)gibi kurallara daha iyi test ve bağlılığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="05ada-113">DI promotes loose coupling of modules in your app and enables better testability and adherence to principles like [SOLID](https://www.weeklydevtips.com/episodes/047).</span></span>

<span data-ttu-id="05ada-114">Uygulamanız DI kullanıyorsa, kullandığınız kapsayıcının ASP.NET Core destekleyip desteklemediğini en iyi şekilde yapmanız olasıdır.</span><span class="sxs-lookup"><span data-stu-id="05ada-114">If your app does use DI, then probably your best course of action is to see if the container you're using supports ASP.NET Core.</span></span> <span data-ttu-id="05ada-115">Bu durumda, bu dosyayı ve tür eşlemelerinizi ve yaşam sürelerini açıklayan özel yapılandırma kurallarınızı kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05ada-115">If so, you may be able to continue using it and your custom configuration rules describing your type mappings and lifetimes.</span></span>

<span data-ttu-id="05ada-116">Her iki durumda da, uygulamanızın ihtiyaçlarını karşılayacağından, ASP.NET Core ile birlikte gelen dı için yerleşik desteği kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="05ada-116">Either way, you should consider using the built-in support for DI that ships with ASP.NET Core, as it may meet your app's needs.</span></span>

## <a name="dependency-injection-in-aspnet-core"></a><span data-ttu-id="05ada-117">ASP.NET Core bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="05ada-117">Dependency injection in ASP.NET Core</span></span>

<span data-ttu-id="05ada-118">ASP.NET Core, uygulamaların DI 'yi kullanacağı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="05ada-118">ASP.NET Core assumes apps will use DI.</span></span> <span data-ttu-id="05ada-119">Yalnızca çerçeveye yerleşik değildir, ancak ASP.NET Core uygulamalarınıza Framework özellikleri desteğini getirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="05ada-119">It's not just built into the framework, but is required in order to bring support for framework features into your ASP.NET Core apps.</span></span> <span data-ttu-id="05ada-120">Uygulama başlangıcında, `ConfigureServices` dı kapsayıcısının (hizmet koleksiyonu/hizmet sağlayıcısı) oluşturup uygulamada ekleyebileceği tüm türlerin kaydolmasından sorumlu olan bir çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="05ada-120">In app startup, a call is made to `ConfigureServices` which is responsible for registering all of the types that the DI container (service collection/service provider) can create and inject in the app.</span></span> <span data-ttu-id="05ada-121">Entity Framework Core, kimlik ve hatta MVC gibi yerleşik ASP.NET Core özellikler, yöntemi içinde hizmet olarak yapılandırarak uygulamaya getirilir `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="05ada-121">Built-in ASP.NET Core features like Entity Framework Core, Identity, and even MVC are brought into the app by configuring them as services in the `ConfigureServices` method.</span></span>

<span data-ttu-id="05ada-122">Uygulamalar, varsayılan uygulamayı kullanmanın yanı sıra özel kapsayıcılar kullanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="05ada-122">In addition to using the default implementation, apps can still use custom containers.</span></span> <span data-ttu-id="05ada-123">[Belgeler, varsayılan hizmet kapsayıcısının nasıl değiştirileceğini anlatmaktadır](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement).</span><span class="sxs-lookup"><span data-stu-id="05ada-123">The [documentation covers how to replace the default service container](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement).</span></span>

<span data-ttu-id="05ada-124">DI ASP.NET Core için temel.</span><span class="sxs-lookup"><span data-stu-id="05ada-124">DI is fundamental to ASP.NET Core.</span></span> <span data-ttu-id="05ada-125">Takımınız bu uygulamada zaten iyi değilse, uygulamanızı aktarmadan önce bunu anlamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="05ada-125">If your team isn't already well-versed in this practice, you'll want to understand it before porting your app.</span></span>

## <a name="references"></a><span data-ttu-id="05ada-126">Başvurular</span><span class="sxs-lookup"><span data-stu-id="05ada-126">References</span></span>

- [<span data-ttu-id="05ada-127">.NET 'e bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="05ada-127">Dependency Injection in .NET</span></span>](../../core/extensions/dependency-injection.md)
- [<span data-ttu-id="05ada-128">ASP.NET Core'da Bağımlılık Ekleme</span><span class="sxs-lookup"><span data-stu-id="05ada-128">Dependency Injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)

>[!div class="step-by-step"]
><span data-ttu-id="05ada-129">[Önceki](serving-static-files.md) 
> [Sonraki](middleware-modules-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="05ada-129">[Previous](serving-static-files.md)
[Next](middleware-modules-handlers.md)</span></span>
