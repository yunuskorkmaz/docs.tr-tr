---
title: .NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | .NET kapsayıcıları ile hedef işletim sistemi
ms.date: 01/07/2019
ms.openlocfilehash: 8bcfa0212f84c575a63f76e05edec1e511cadc36
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772009"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="a962a-103">.NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?</span><span class="sxs-lookup"><span data-stu-id="a962a-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="a962a-104">Docker tarafından desteklenen işletim sistemlerinin farklılığının yanı sıra .NET Framework ile .NET Core arasındaki farklılıklar söz konusu olduğunda, kullanmakta olduğunuz çerçeveye bağlı olarak belirli bir işletim sistemini ve belirli sürümleri hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="a962a-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="a962a-105">Windows için Windows Server Core veya Windows nano Server kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a962a-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="a962a-106">Bu Windows sürümleri, sırasıyla .NET Framework veya .NET Core tarafından gerekebilecek, farklı Özellikler (Windows Server çekirdeği 'nde IIS ve Kestrel gibi şirket içinde barındırılan bir Web sunucusu) sağlar.</span><span class="sxs-lookup"><span data-stu-id="a962a-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="a962a-107">Linux için, resmi .NET Docker görüntülerinde (Deklik gibi) Çoklu destekler mevcuttur ve desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a962a-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="a962a-108">Şekil 3-1 ' de, kullanılan .NET Framework 'e bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a962a-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Eski .NET Framework uygulamalar dağıtıldığında, eski uygulamalarla ve IIS ile uyumlu Windows Server çekirdeğini hedeflemek için daha büyük bir görüntü vardır.](./media/image1.png)

<span data-ttu-id="a962a-113">**Şekil 3-1.**</span><span class="sxs-lookup"><span data-stu-id="a962a-113">**Figure 3-1.**</span></span> <span data-ttu-id="a962a-114">.NET Framework sürümüne bağlı olarak hedeflenecek işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="a962a-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="a962a-115">Ayrıca, farklı bir Linux veya Microsoft tarafından sağlanmayan sürümlere sahip bir görüntü istediğiniz durumlarda kendi Docker görüntünüzü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a962a-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="a962a-116">Örneğin, Docker için olmayan-yaygın bir senaryo olan geleneksel .NET Framework ve Windows Server Core üzerinde çalışan ASP.NET Core bir görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a962a-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a962a-117">Windows Server çekirdek görüntülerini kullanırken, tam Windows görüntüleriyle karşılaştırıldığında bazı dll 'Lerin eksik olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a962a-117">When using Windows Server Core images, you might find that some DLLs are missing, when compared to full Windows images.</span></span> <span data-ttu-id="a962a-118">Bu sorunu, bu [GitHub açıklamasında](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)belirtildiği gibi, görüntü derleme zamanında eksik dosyaları ekleyerek özel bir sunucu çekirdeği görüntüsü oluşturarak çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a962a-118">You might be able to solve this problem by creating a custom Server Core image, adding the missing files at image build time, as mentioned in this [GitHub comment](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).</span></span>

<span data-ttu-id="a962a-119">Resim adını Dockerfile dosyanıza eklediğinizde, aşağıdaki örneklerde olduğu gibi, kullandığınız etikete bağlı olarak işletim sistemini ve sürümü seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a962a-119">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

| <span data-ttu-id="a962a-120">Görüntü</span><span class="sxs-lookup"><span data-stu-id="a962a-120">Image</span></span> | <span data-ttu-id="a962a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a962a-121">Comments</span></span> |
|-------|----------|
| <span data-ttu-id="a962a-122">mcr.microsoft.com/dotnet/core/runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="a962a-122">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span> | <span data-ttu-id="a962a-123">.NET Core 2,2 Multi-Architecture: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler.</span><span class="sxs-lookup"><span data-stu-id="a962a-123">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> |
| <span data-ttu-id="a962a-124">mcr.microsoft.com/dotnet/core/aspnet:2.2</span><span class="sxs-lookup"><span data-stu-id="a962a-124">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span> | <span data-ttu-id="a962a-125">ASP.NET Core 2,2 Multi-Architecture: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler.</span><span class="sxs-lookup"><span data-stu-id="a962a-125">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> <br/> <span data-ttu-id="a962a-126">Aspnetcore görüntüsünün ASP.NET Core için birkaç iyileştirmesi vardır.</span><span class="sxs-lookup"><span data-stu-id="a962a-126">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span> |
| <span data-ttu-id="a962a-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span><span class="sxs-lookup"><span data-stu-id="a962a-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span> | <span data-ttu-id="a962a-128">.NET Core 2,2 çalışma zamanı-yalnızca Linux alp Deon</span><span class="sxs-lookup"><span data-stu-id="a962a-128">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span> |
| <span data-ttu-id="a962a-129">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="a962a-129">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span> | <span data-ttu-id="a962a-130">.NET Core 2,2 çalışma zamanı-yalnızca Windows nano Server 'da (Windows Server sürüm 1803)</span><span class="sxs-lookup"><span data-stu-id="a962a-130">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span> |

## <a name="additional-resources"></a><span data-ttu-id="a962a-131">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a962a-131">Additional resources</span></span>

- <span data-ttu-id="a962a-132">**BitmapDecoder, eksik WindowsCodecsExt. dll nedeniyle başarısız oluyor (GitHub sorunu)**</span><span class="sxs-lookup"><span data-stu-id="a962a-132">**BitmapDecoder fails due to missing WindowsCodecsExt.dll (GitHub issue)**</span></span>  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> <span data-ttu-id="a962a-133">[Önceki](container-framework-choice-factors.md)
> [İleri](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="a962a-133">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
