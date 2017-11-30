---
title: "Hedef .NET kapsayıcıları ile hangi işletim sistemi"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Hedef .NET kapsayıcıları ile hangi işletim sistemi"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="e1520-104">Hedef .NET kapsayıcıları ile hangi işletim sistemi</span><span class="sxs-lookup"><span data-stu-id="e1520-104">What OS to target with .NET containers</span></span>

<span data-ttu-id="e1520-105">Docker ve .NET Framework ve .NET Core arasındaki farklar tarafından desteklenen işletim sistemleri seviyelerine verildiğinde, belirli bir işletim sistemi ve kullandığınız framework bağlı olarak belirli sürümlerini hedefleyen.</span><span class="sxs-lookup"><span data-stu-id="e1520-105">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="e1520-106">Windows, Windows Server Core veya Windows Nano Server kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1520-106">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="e1520-107">Bu Windows sürümlerini .NET Framework veya .NET Core tarafından sırasıyla gerçekleştirmeniz gerekebilecek farklı özellikleri (Windows Server Core Kestrel Nano Server gibi kendi kendini barındıran web sunucusu yerine IIS) sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1520-107">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="e1520-108">Linux için kullanılabilir ve desteklenen (Debian gibi) resmi .NET Docker görüntülerinde birden çok distro'lar.</span><span class="sxs-lookup"><span data-stu-id="e1520-108">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="e1520-109">Şekil 3-1'de kullanılan .NET framework bağlı olarak olası işletim sistemi sürümü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1520-109">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="e1520-110">**Şekil 3-1.**</span><span class="sxs-lookup"><span data-stu-id="e1520-110">**Figure 3-1.**</span></span> <span data-ttu-id="e1520-111">.NET framework sürümleri bağlı olarak hedeflemek için işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="e1520-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="e1520-112">Farklı Linux distro kullanmak istediğiniz veya görüntü Microsoft tarafından sağlanmayan sürümleriyle istediğiniz durumlarda de kendi Docker görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1520-112">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="e1520-113">Örneğin, ASP.NET geleneksel .NET Framework ve Docker değil pek yaygın senaryodur Windows Server Core üzerinde çalışan temel bir görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1520-113">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="e1520-114">Görüntü adı Dockerfile dosyanızı eklediğinizde, işletim sistemi ve sürümüne bağlı olarak, aşağıdaki örneklerde olduğu gibi kullandığınız etiketi seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1520-114">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="e1520-115">Microsoft /**dotnet:2.0.0-çalışma zamanı-jessie**</span><span class="sxs-lookup"><span data-stu-id="e1520-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

-   <span data-ttu-id="e1520-116">Microsoft /**dotnet:2.0.0-çalışma zamanı-nanoserver-1709**</span><span class="sxs-lookup"><span data-stu-id="e1520-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span></span> 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   <span data-ttu-id="e1520-117">Microsoft /**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="e1520-117">microsoft/**aspnetcore:2.0**</span></span>
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
<span data-ttu-id="e1520-118">[Önceki] (kapsayıcı-framework-seçim-factors.md) [sonraki] (resmi-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="e1520-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>
