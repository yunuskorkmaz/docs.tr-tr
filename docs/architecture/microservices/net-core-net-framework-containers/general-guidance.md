---
title: Genel kılavuz
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Genel rehberlik
ms.date: 01/13/2021
ms.openlocfilehash: 4fd2d936c524cb3e5ae463038eaffe88b459d2bd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187957"
---
# <a name="general-guidance"></a><span data-ttu-id="75406-103">Genel kılavuz</span><span class="sxs-lookup"><span data-stu-id="75406-103">General guidance</span></span>

<span data-ttu-id="75406-104">Bu bölümde, .NET 5 veya .NET Framework ne zaman seçeceğiniz hakkında bir Özet sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75406-104">This section provides a summary of when to choose .NET 5 or .NET Framework.</span></span> <span data-ttu-id="75406-105">İzleyen bölümlerde bu seçimler hakkında daha fazla ayrıntı sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="75406-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="75406-106">Şu durumlarda Kapsayıcılı Docker sunucu uygulamanızda .NET 5 ' i Linux veya Windows kapsayıcılarıyla birlikte kullanın:</span><span class="sxs-lookup"><span data-stu-id="75406-106">Use .NET 5, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="75406-107">Platformlar arası gereksinimleriniz var.</span><span class="sxs-lookup"><span data-stu-id="75406-107">You have cross-platform needs.</span></span> <span data-ttu-id="75406-108">Örneğin, hem Linux hem de Windows kapsayıcılarını kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="75406-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="75406-109">Uygulama mimariniz mikro hizmetleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="75406-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="75406-110">Kapsayıcıları hızlı bir şekilde başlatmanız ve bir kapsayıcı başına küçük bir ayak izi, maliyetlerinizi düşürmek için donanım birimi başına daha iyi yoğunluk veya daha fazla kapsayıcı elde etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="75406-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="75406-111">Kısacası, yeni Kapsayıcılı .NET uygulamaları oluşturduğunuzda, .NET 5 ' i varsayılan seçenek olarak düşünmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="75406-111">In short, when you create new containerized .NET applications, you should consider .NET 5 as the default choice.</span></span> <span data-ttu-id="75406-112">Birçok avantajı vardır ve kapsayıcıların FI ve çalışma tarzıyla en iyi şekilde uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="75406-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="75406-113">.NET 5 kullanmanın bir avantajı, aynı makine içindeki uygulamalar için yan yana .NET sürümlerini çalıştırabilmeniz.</span><span class="sxs-lookup"><span data-stu-id="75406-113">An extra benefit of using .NET 5 is that you can run side-by-side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="75406-114">Bu avantaj, kapsayıcılar kullanmayan sunucular veya VM 'Ler için daha önemlidir çünkü kapsayıcılar, uygulamanın ihtiyaç duyacağı .NET sürümlerini yalıtır.</span><span class="sxs-lookup"><span data-stu-id="75406-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="75406-115">(Temel alınan IŞLETIM sistemiyle uyumlu oldukları sürece.)</span><span class="sxs-lookup"><span data-stu-id="75406-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="75406-116">Kapsayıcılı Docker sunucu uygulamanız için .NET Framework şu durumlarda kullanın:</span><span class="sxs-lookup"><span data-stu-id="75406-116">Use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="75406-117">Uygulamanız Şu anda .NET Framework kullanıyor ve Windows üzerinde güçlü bağımlılıklara sahip.</span><span class="sxs-lookup"><span data-stu-id="75406-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="75406-118">.NET 5 tarafından desteklenmeyen Windows API 'Lerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="75406-118">You need to use Windows APIs that are not supported by .NET 5.</span></span>

- <span data-ttu-id="75406-119">.NET 5 için kullanılamayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="75406-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET 5.</span></span>

<span data-ttu-id="75406-120">Docker üzerinde .NET Framework kullanmak, dağıtım sorunlarını en aza indirerek dağıtım deneyimlerinizi iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="75406-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="75406-121">Bu ["yükseltme ve kaydırma" senaryosu](https://aka.ms/liftandshiftwithcontainersebook) , ASP.net WEBFORMS, MVC Web Apps veya WCF (Windows Communication Foundation) Hizmetleri gibi geleneksel .NET Framework geliştirilmiş eski uygulamaları kapsayımak için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="75406-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="75406-122">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="75406-122">Additional resources</span></span>

- <span data-ttu-id="75406-123">**E-kitap: Azure ve Windows kapsayıcıları ile mevcut .NET Framework uygulamaları modernleştirin**</span><span class="sxs-lookup"><span data-stu-id="75406-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    <https://aka.ms/liftandshiftwithcontainersebook>

- <span data-ttu-id="75406-124">**Örnek uygulamalar: Windows kapsayıcıları kullanarak eski ASP.NET Web uygulamalarını modernleştirme**</span><span class="sxs-lookup"><span data-stu-id="75406-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
><span data-ttu-id="75406-125">[Önceki](index.md) 
> [Sonraki](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="75406-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
