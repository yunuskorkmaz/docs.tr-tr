---
title: Hedef .NET kapsayıcıları ile hangi işletim sistemi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Hedef .NET kapsayıcıları ile hangi işletim sistemi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: b2ae1d2e732f152133dd8a8757b955e05cdd88eb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677818"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="e6e9e-103">Hedef .NET kapsayıcıları ile hangi işletim sistemi</span><span class="sxs-lookup"><span data-stu-id="e6e9e-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="e6e9e-104">Docker ve .NET Framework ve .NET Core arasındaki farklar tarafından desteklenen işletim sistemleri yelpazesi göz önünde bulundurulduğunda, belirli bir işletim sistemi ve kullanmakta olduğunuz framework bağlı olarak belirli sürümlerini hedefleyen.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="e6e9e-105">Windows için Windows Server Core veya Windows Nano sunucu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="e6e9e-106">Bu Windows sürümleri (Windows Server Core Kestrel Nano Sunucu'da gibi bir şirket içinde barındırılan web sunucusu yerine IIS) .NET Framework veya .NET Core tarafından sırasıyla gerekebilecek farklı özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="e6e9e-107">Linux için birden çok dağıtım paketlerini kullanılabilir ve (Debian gibi) resmi .NET Docker görüntüleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="e6e9e-108">Şekil 3-1'de kullanılan .NET framework bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Eski .NET Framework uygulamaları, sahip olduğunuz Windows Server Core hede için dağıtırken uyumlu eski uygulamaları ile IIS, daha büyük bir görüntü sahiptir.](./media/image1.png)

<span data-ttu-id="e6e9e-113">**Şekil 3-1.**</span><span class="sxs-lookup"><span data-stu-id="e6e9e-113">**Figure 3-1.**</span></span> <span data-ttu-id="e6e9e-114">Bağlı olarak .NET Framework sürümlerini hedeflemek için işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="e6e9e-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="e6e9e-115">Farklı bir Linux distro kullanmak istediğiniz veya görüntü Microsoft tarafından sağlanmayan sürümleriyle istediğiniz durumlarda kendi Docker görüntünüzü de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="e6e9e-116">Örneğin, geleneksel .NET Framework ve Docker olmayan şekilde yaygın senaryodur Windows Server Core üzerinde çalışan ASP.NET Core ile bir görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="e6e9e-117">Görüntü adı, Dockerfile dosyasına eklediğinizde, işletim sistemi ve sürümüne göre aşağıdaki örneklerde olduğu gibi kullanın etiketi seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6e9e-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="e6e9e-118">Görüntü</span><span class="sxs-lookup"><span data-stu-id="e6e9e-118">Image</span></span></th>
<th><span data-ttu-id="e6e9e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6e9e-119">Comments</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td><span data-ttu-id="e6e9e-120">Microsoft / dotnet:2.1-çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e6e9e-120">microsoft/dotnet:2.1-runtime</span></span></td>
<td><span data-ttu-id="e6e9e-121">.NET core 2.1 çok mimari: destekleyen Linux ve Docker konağı bağlı olarak Windows Nano sunucu.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-121">.NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e6e9e-122">Microsoft / dotnet:2.1-aspnetcore-çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e6e9e-122">microsoft/dotnet:2.1-aspnetcore-runtime</span></span></td>
<td><p><span data-ttu-id="e6e9e-123">ASP.NET Core 2.1 çok mimari: destekleyen Linux ve Docker konağı bağlı olarak Windows Nano sunucu.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-123">ASP.NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></p>
<p><span data-ttu-id="e6e9e-124">ASP.NET Core için birkaç en iyi duruma getirme aspnetcore görüntüsü vardır.</span><span class="sxs-lookup"><span data-stu-id="e6e9e-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e6e9e-125">Microsoft / dotnet:2.1-aspnetcore-çalışma zamanı-alpine</span><span class="sxs-lookup"><span data-stu-id="e6e9e-125">microsoft/dotnet:2.1-aspnetcore-runtime-alpine</span></span></td>
<td><span data-ttu-id="e6e9e-126">.NET core 2.1 çalışma zamanı üzerinde Linux Alpine distro yalnızca</span><span class="sxs-lookup"><span data-stu-id="e6e9e-126">.NET Core 2.1 runtime-only on Linux Alpine distro</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e6e9e-127">Microsoft / dotnet:2.1-aspnetcore-çalışma zamanı-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="e6e9e-127">microsoft/dotnet:2.1-aspnetcore-runtime-nanoserver-1803</span></span></td>
<td><span data-ttu-id="e6e9e-128">.NET core 2.1 (Windows Server sürümü 1803) Windows Nano Sunucu'da salt çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e6e9e-128">.NET Core 2.1 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
<span data-ttu-id="e6e9e-129">[Önceki](container-framework-choice-factors.md)
[İleri](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="e6e9e-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
