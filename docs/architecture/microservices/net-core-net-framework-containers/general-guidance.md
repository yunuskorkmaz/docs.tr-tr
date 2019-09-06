---
title: Genel rehber
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Genel rehberlik
ms.date: 09/11/2018
ms.openlocfilehash: 0981cb16d5aa2036391caba0cf6ad3ac5c44ed6f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296530"
---
# <a name="general-guidance"></a><span data-ttu-id="b1831-103">Genel rehber</span><span class="sxs-lookup"><span data-stu-id="b1831-103">General guidance</span></span>

<span data-ttu-id="b1831-104">Bu bölüm, ne zaman .NET Core veya .NET Framework seçme hakkında bir Özet sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1831-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="b1831-105">İzleyen bölümlerde bu seçimler hakkında daha fazla ayrıntı sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="b1831-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="b1831-106">Şu durumlarda Kapsayıcılı Docker sunucu uygulamanızda .NET Core 'u Linux veya Windows kapsayıcıları ile kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b1831-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="b1831-107">Platformlar arası gereksinimleriniz var.</span><span class="sxs-lookup"><span data-stu-id="b1831-107">You have cross-platform needs.</span></span> <span data-ttu-id="b1831-108">Örneğin, hem Linux hem de Windows kapsayıcılarını kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b1831-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="b1831-109">Uygulama mimariniz mikro hizmetleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="b1831-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="b1831-110">Kapsayıcıları hızlı bir şekilde başlatmanız ve bir kapsayıcı başına küçük bir ayak izi, maliyetlerinizi düşürmek için donanım birimi başına daha iyi yoğunluk veya daha fazla kapsayıcı elde etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1831-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="b1831-111">Kısacası, yeni Kapsayıcılı .NET uygulamaları oluşturduğunuzda, .NET Core 'u varsayılan seçim olarak düşünmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1831-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="b1831-112">Birçok avantajı vardır ve kapsayıcıların FI ve çalışma tarzıyla en iyi şekilde uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1831-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="b1831-113">.NET Core kullanmanın ek avantajları, aynı makine içindeki uygulamalar için yan yana .NET sürümlerini çalıştırabilmeniz.</span><span class="sxs-lookup"><span data-stu-id="b1831-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="b1831-114">Bu avantaj, kapsayıcılar kullanmayan sunucular veya VM 'Ler için daha önemlidir çünkü kapsayıcılar, uygulamanın ihtiyaç duyacağı .NET sürümlerini yalıtır.</span><span class="sxs-lookup"><span data-stu-id="b1831-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="b1831-115">(Temel alınan IŞLETIM sistemiyle uyumlu oldukları sürece.)</span><span class="sxs-lookup"><span data-stu-id="b1831-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="b1831-116">Kapsayıcılı Docker sunucu uygulamanız için .NET Framework şu durumlarda kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b1831-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="b1831-117">Uygulamanız Şu anda .NET Framework kullanıyor ve Windows üzerinde güçlü bağımlılıklara sahip.</span><span class="sxs-lookup"><span data-stu-id="b1831-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="b1831-118">.NET Core tarafından desteklenmeyen Windows API 'Lerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1831-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="b1831-119">.NET Core için kullanılamayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1831-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="b1831-120">Docker üzerinde .NET Framework kullanmak, dağıtım sorunlarını en aza indirerek dağıtım deneyimlerinizi iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b1831-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="b1831-121">Bu ["yükseltme ve kaydırma" senaryosu](https://aka.ms/liftandshiftwithcontainersebook) , ASP.net WEBFORMS, MVC Web Apps veya WCF (Windows Communication Foundation) Hizmetleri gibi geleneksel .NET Framework geliştirilmiş eski uygulamaları kapsayımak için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b1831-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b1831-122">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b1831-122">Additional resources</span></span>

- <span data-ttu-id="b1831-123">**E-kitap Azure ve Windows kapsayıcıları ile mevcut .NET Framework uygulamaları modernleştirin**</span><span class="sxs-lookup"><span data-stu-id="b1831-123">**eBook: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

- <span data-ttu-id="b1831-124">**Örnek uygulamalar: Windows kapsayıcıları kullanarak eski ASP.NET Web uygulamalarını modernleştirme**</span><span class="sxs-lookup"><span data-stu-id="b1831-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
><span data-ttu-id="b1831-125">[Önceki](index.md)İleri
>[](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="b1831-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
