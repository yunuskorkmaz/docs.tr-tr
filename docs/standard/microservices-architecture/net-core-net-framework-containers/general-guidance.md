---
title: Genel yönergeler
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Genel yönergeler
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: bd654c23cf8a8d0986575642ef25d6864251a4e4
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104085"
---
# <a name="general-guidance"></a><span data-ttu-id="903b3-103">Genel yönergeler</span><span class="sxs-lookup"><span data-stu-id="903b3-103">General guidance</span></span>

<span data-ttu-id="903b3-104">Bu bölümde, .NET Core veya .NET Framework seçmek ne zaman bir özetini sunar.</span><span class="sxs-lookup"><span data-stu-id="903b3-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="903b3-105">Aşağıdaki bölümlerde bu seçenekler hakkında daha fazla ayrıntı sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="903b3-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="903b3-106">.NET Core, Linux veya Windows kapsayıcıları kapsayıcılı Docker server uygulamanız için kullanmanız gerekir zaman:</span><span class="sxs-lookup"><span data-stu-id="903b3-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="903b3-107">Platformlar arası gereksinimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="903b3-107">You have cross-platform needs.</span></span> <span data-ttu-id="903b3-108">Örneğin, Linux ve Windows kapsayıcılar kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="903b3-108">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="903b3-109">Uygulama Mimarinizi mikro üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="903b3-109">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="903b3-110">Kapsayıcıları Hızlı Başlat ve, maliyetleri azaltmak için daha iyi yoğunluğu elde etmek için kapsayıcı ya da daha fazla kapsayıcı donanım birim başına başına küçük bir yer istediğiniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="903b3-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="903b3-111">Kısacası, yeni kapsayıcılı .NET uygulamaları oluşturduğunuzda varsayılan seçenek olarak .NET Core düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="903b3-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="903b3-112">Birçok avantaj vardır ve kapsayıcıları felsefesi ve çalışma stilini en uygun.</span><span class="sxs-lookup"><span data-stu-id="903b3-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="903b3-113">.NET Core kullanmanın ek bir faydası aynı makinedeki uygulamaları için yan yana .NET sürümleri çalıştırabilirsiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="903b3-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="903b3-114">Uygulamanın gerekir .NET sürümlerinin kapsayıcıları yalıtmak için bu avantajı sunucuları veya kapsayıcıları, kullanmayın VM'ler için daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="903b3-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="903b3-115">(Temel işletim sistemiyle uyumlu olduklarını sürece.)</span><span class="sxs-lookup"><span data-stu-id="903b3-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="903b3-116">İle Windows kapsayıcıları, .NET Framework kapsayıcılı Docker server uygulamanız için kullanması gereken zaman:</span><span class="sxs-lookup"><span data-stu-id="903b3-116">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="903b3-117">Uygulamanız şu anda .NET Framework kullanır ve Windows'da güçlü bağımlılıklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="903b3-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="903b3-118">.NET Core tarafından desteklenmeyen Windows API'leri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="903b3-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="903b3-119">Üçüncü taraf .NET kitaplıklarına veya .NET Core için kullanılabilir değil NuGet paketlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="903b3-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="903b3-120">.NET Framework üzerinde Docker kullanarak dağıtım deneyimlerinizi dağıtım sorunlarını en aza indirerek artırabilir.</span><span class="sxs-lookup"><span data-stu-id="903b3-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="903b3-121">Bu [ *"kaldırın ve shift" senaryo* ](https://aka.ms/liftandshiftwithcontainersebook) ASP.NET WebForms, MVC web uygulamaları veya WCF (gibi geleneksel .NET Framework ile ilk olarak geliştirilen eski uygulamaları containerizing için önemlidir Windows Communication Foundation) Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="903b3-121">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="903b3-122">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="903b3-122">Additional resources</span></span>

-   <span data-ttu-id="903b3-123">**e-kitap: Azure ve Windows kapsayıcıları ile var olan .NET Framework uygulamaları Modernize**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="903b3-123">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="903b3-124">**Örnek uygulamalar: Modernization Windows kapsayıcıları kullanarak eski ASP.NET web uygulamaları**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="903b3-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="903b3-125">[Önceki](index.md)
[sonraki](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="903b3-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
