---
title: .NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Hedef .NET kapsayıcıları ile hangi işletim sistemi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 14a0fb7cd9ecb8dfd5369da6f6bd5b47b4aea37a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58921305"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="881f5-103">.NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?</span><span class="sxs-lookup"><span data-stu-id="881f5-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="881f5-104">Docker ve .NET Framework ve .NET Core arasındaki farklar tarafından desteklenen işletim sistemleri yelpazesi göz önünde bulundurulduğunda, belirli bir işletim sistemi ve kullanmakta olduğunuz framework bağlı olarak belirli sürümlerini hedefleyen.</span><span class="sxs-lookup"><span data-stu-id="881f5-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="881f5-105">Windows için Windows Server Core veya Windows Nano sunucu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="881f5-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="881f5-106">Bu Windows sürümleri (Windows Server Core Kestrel Nano Sunucu'da gibi bir şirket içinde barındırılan web sunucusu yerine IIS) .NET Framework veya .NET Core tarafından sırasıyla gerekebilecek farklı özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="881f5-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="881f5-107">Linux için birden çok dağıtım paketlerini kullanılabilir ve (Debian gibi) resmi .NET Docker görüntüleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="881f5-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="881f5-108">Şekil 3-1'de kullanılan .NET framework bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="881f5-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Windows Server Core hedeflemek için sahip olduğunuz eski .NET Framework uygulamaları dağıtırken uyumlu eski uygulamaları ile IIS, daha büyük bir görüntü sahiptir.](./media/image1.png)

<span data-ttu-id="881f5-113">**Şekil 3-1.**</span><span class="sxs-lookup"><span data-stu-id="881f5-113">**Figure 3-1.**</span></span> <span data-ttu-id="881f5-114">Bağlı olarak .NET Framework sürümlerini hedeflemek için işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="881f5-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="881f5-115">Farklı bir Linux distro kullanmak istediğiniz veya görüntü Microsoft tarafından sağlanmayan sürümleriyle istediğiniz durumlarda kendi Docker görüntünüzü de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="881f5-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="881f5-116">Örneğin, geleneksel .NET Framework ve Docker olmayan şekilde yaygın senaryodur Windows Server Core üzerinde çalışan ASP.NET Core ile bir görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="881f5-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="881f5-117">Görüntü adı, Dockerfile dosyasına eklediğinizde, işletim sistemi ve sürümüne göre aşağıdaki örneklerde olduğu gibi kullanın etiketi seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="881f5-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="881f5-118">Görüntü</span><span class="sxs-lookup"><span data-stu-id="881f5-118">Image</span></span></th>
<th><span data-ttu-id="881f5-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="881f5-119">Comments</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td><span data-ttu-id="881f5-120">MCR.microsoft.com/dotnet/Core/Runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="881f5-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span></td>
<td><span data-ttu-id="881f5-121">.NET core 2.2 çok mimarisi: Docker konağı bağlı olarak, Linux ve Windows Nano sunucu destekler.</span><span class="sxs-lookup"><span data-stu-id="881f5-121">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="881f5-122">MCR.microsoft.com/dotnet/Core/ASPNET:2.2</span><span class="sxs-lookup"><span data-stu-id="881f5-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span></td>
<td><p><span data-ttu-id="881f5-123">ASP.NET Core 2.2 çok mimarisi: Docker konağı bağlı olarak, Linux ve Windows Nano sunucu destekler.</span><span class="sxs-lookup"><span data-stu-id="881f5-123">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></p>
<p><span data-ttu-id="881f5-124">ASP.NET Core için birkaç en iyi duruma getirme aspnetcore görüntüsü vardır.</span><span class="sxs-lookup"><span data-stu-id="881f5-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="881f5-125">MCR.microsoft.com/dotnet/Core/ASPNET:2.2-Alpine</span><span class="sxs-lookup"><span data-stu-id="881f5-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span></td>
<td><span data-ttu-id="881f5-126">.NET core 2.2 Alpine Linux distro'üzerinde salt çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="881f5-126">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="881f5-127">MCR.microsoft.com/dotnet/Core/ASPNET:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="881f5-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span></td>
<td><span data-ttu-id="881f5-128">.NET core 2.2 (Windows Server sürümü 1803) Windows Nano Sunucu'da salt çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="881f5-128">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span></td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> <span data-ttu-id="881f5-129">[Önceki](container-framework-choice-factors.md)
> [İleri](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="881f5-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>