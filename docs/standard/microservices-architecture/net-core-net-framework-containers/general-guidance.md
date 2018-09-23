---
title: Genel rehberlik
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Genel rehberlik
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: e77065614423cd2e7fdb51258a8c7650280d0400
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537832"
---
# <a name="general-guidance"></a><span data-ttu-id="2b4e4-103">Genel rehberlik</span><span class="sxs-lookup"><span data-stu-id="2b4e4-103">General guidance</span></span>

<span data-ttu-id="2b4e4-104">Bu bölümde, ne zaman .NET Core veya .NET Framework seçin, bir özetini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="2b4e4-105">Aşağıdaki bölümlerde bu seçenekler hakkında daha fazla bilgi sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="2b4e4-106">.NET Core, Linux veya Windows kapsayıcıları ile kapsayıcılı Docker sunucusu uygulamanız için kullanmanız gereken zaman:</span><span class="sxs-lookup"><span data-stu-id="2b4e4-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="2b4e4-107">Platformlar arası ihtiyaçları vardır.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-107">You have cross-platform needs.</span></span> <span data-ttu-id="2b4e4-108">Örneğin, hem Linux hem de Windows kapsayıcıları kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-108">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="2b4e4-109">Uygulama mimarinizin üzerinde mikro hizmetler temel alır.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-109">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="2b4e4-110">Kapsayıcıları Hızlı Başlat ve maliyetlerinizi azaltmak için daha iyi yoğunluklu elde etmek için kapsayıcı ya da daha fazla kapsayıcı donanım birim başına küçük ayak izine gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="2b4e4-111">Kısacası, yeni kapsayıcılı .NET uygulamaları oluşturduğunuzda varsayılan seçenek olarak .NET Core düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="2b4e4-112">Kapsayıcıları felsefesi ve çalışma tarzıyla ile gereksinimlerine ve pek çok faydası vardır.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="2b4e4-113">.NET Core kullanmanın ek bir avantaj, aynı makineye içindeki uygulamalar için .NET sürümleri yan yana çalıştırabileceğiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="2b4e4-114">Uygulama gerektiren .NET sürümlerini kapsayıcıları yalıtmak için bu sunucuları veya kapsayıcılar, kullanmayan sanal makineleri için önemli bir avantajdır.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="2b4e4-115">(Bunlar temel işletim sistemi ile uyumlu olduğu sürece.)</span><span class="sxs-lookup"><span data-stu-id="2b4e4-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="2b4e4-116">.NET Framework kapsayıcılı Docker sunucusu uygulamanız için kullanması gereken zaman:</span><span class="sxs-lookup"><span data-stu-id="2b4e4-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="2b4e4-117">Uygulamanız şu anda kullandığı .NET Framework ve Windows üzerinde güçlü bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="2b4e4-118">.NET Core tarafından desteklenmeyen bir Windows API'leri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="2b4e4-119">Üçüncü taraf .NET kitaplıkları veya .NET Core için kullanılabilir değil, NuGet paketlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="2b4e4-120">Docker üzerinde .NET Framework kullanarak dağıtım sorunlarını en aza indirerek, dağıtım deneyimleri geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="2b4e4-121">Bu ["kaldırma ve kaydırma" senaryo](https://aka.ms/liftandshiftwithcontainersebook) ASP.NET WebForms, MVC web uygulamaları veya WCF (Windows Communication Foundation gibi ilk olarak geleneksel .NET Framework ile geliştirilen eski uygulamaları kapsayıcılı hale getirmek için önemlidir ) Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="2b4e4-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2b4e4-122">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2b4e4-122">Additional resources</span></span>

-   <span data-ttu-id="2b4e4-123">**e-kitap: Azure ve Windows kapsayıcıları ile mevcut .NET Framework uygulamalarını Modernleştirin**</span><span class="sxs-lookup"><span data-stu-id="2b4e4-123">**eBook: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

-   <span data-ttu-id="2b4e4-124">**Örnek uygulamalar: Windows kapsayıcıları kullanarak eski ASP.NET web uygulama Modernizasyonu**</span><span class="sxs-lookup"><span data-stu-id="2b4e4-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing


>[!div class="step-by-step"]
<span data-ttu-id="2b4e4-125">[Önceki](index.md)
[İleri](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="2b4e4-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
