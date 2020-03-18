---
title: Genel kılavuz
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Genel rehberlik
ms.date: 09/11/2018
ms.openlocfilehash: 2fa66d7593b764a8df4d9acc20f93d3f8fb26174
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089643"
---
# <a name="general-guidance"></a><span data-ttu-id="f1582-103">Genel kılavuz</span><span class="sxs-lookup"><span data-stu-id="f1582-103">General guidance</span></span>

<span data-ttu-id="f1582-104">Bu bölümde ,NET Core veya .NET Framework ne zaman seçileceklerinin bir özetini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1582-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="f1582-105">Takip eden bölümlerde bu seçenekler hakkında daha fazla bilgi sağlarız.</span><span class="sxs-lookup"><span data-stu-id="f1582-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="f1582-106">Kapsayıcı Docker sunucu uygulamanız için Linux veya Windows Kapsayıcıları ile .NET Core'u şu zaman kullanmalısınız:</span><span class="sxs-lookup"><span data-stu-id="f1582-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="f1582-107">Platform ötesi ihtiyaçların var.</span><span class="sxs-lookup"><span data-stu-id="f1582-107">You have cross-platform needs.</span></span> <span data-ttu-id="f1582-108">Örneğin, hem Linux hem de Windows Kapsayıcıları kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f1582-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="f1582-109">Uygulama mimariniz mikro hizmetlere dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1582-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="f1582-110">Maliyetlerinizi düşürmek için kapsayıcıları hızlı başlatmanız ve donanım birimi başına daha iyi yoğunluk veya daha fazla kapsayıcı elde etmek için konteyner başına küçük bir ayak izi istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1582-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="f1582-111">Kısacası, yeni kapsayıcı .NET uygulamaları oluşturduğunuzda, .NET Core'u varsayılan seçenek olarak düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f1582-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="f1582-112">Birçok faydası vardır ve konteyner felsefesi ve çalışma tarzı ile en iyi uyuyor.</span><span class="sxs-lookup"><span data-stu-id="f1582-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="f1582-113">.NET Core'u kullanmanın bir diğer avantajı da, aynı makinedeki uygulamalar için yan yana .NET sürümlerini çalıştırabiliyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1582-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="f1582-114">Kapsayıcılar .NET'in uygulamanın ihtiyaç duyduğu sürümleriya yalıttığından, bu avantaj kapsayıcıları kullanmayan sunucular veya VM'ler için daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f1582-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="f1582-115">(Temel işletim sistemi yle uyumlu oldukları sürece.)</span><span class="sxs-lookup"><span data-stu-id="f1582-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="f1582-116">Kapsayıcı Docker sunucu uygulamanız için .NET Framework'u şu zaman kullanmalısınız:</span><span class="sxs-lookup"><span data-stu-id="f1582-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="f1582-117">Uygulamanız şu anda .NET Framework kullanır ve Windows üzerinde güçlü bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="f1582-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="f1582-118">.NET Core tarafından desteklenmeyen Windows API'lerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1582-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="f1582-119">.NET Core için kullanılamayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1582-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="f1582-120">Docker'da .NET Framework'ü kullanmak, dağıtım sorunlarını en aza indirerek dağıtım deneyimlerinizi artırabilir.</span><span class="sxs-lookup"><span data-stu-id="f1582-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="f1582-121">Bu ["kaldırma ve kaydırma" senaryosu,](https://aka.ms/liftandshiftwithcontainersebook) web formları, MVC web uygulamaları veya WCF (Windows Communication Foundation) hizmetleri ASP.NET gibi geleneksel .NET Framework ile geliştirilen eski uygulamaları konteynerleştirmek için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f1582-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f1582-122">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f1582-122">Additional resources</span></span>

- <span data-ttu-id="f1582-123">**E-kitap: Azure ve Windows Kapsayıcıları ile mevcut .NET Framework uygulamalarını modernize edin**</span><span class="sxs-lookup"><span data-stu-id="f1582-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

- <span data-ttu-id="f1582-124">**Örnek uygulamalar: Windows Kapsayıcıları kullanılarak eski ASP.NET web uygulamalarının modernizasyonu**</span><span class="sxs-lookup"><span data-stu-id="f1582-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
><span data-ttu-id="f1582-125">[Önceki](index.md)
>[Sonraki](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="f1582-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
