---
title: .NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | .NET kapsayıcıları ile hedef işletim sistemi
ms.date: 01/13/2021
ms.openlocfilehash: 1b914d9afca9ade37f13e639f73001b91f338d26
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187995"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="dafbd-103">.NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?</span><span class="sxs-lookup"><span data-stu-id="dafbd-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="dafbd-104">Docker tarafından desteklenen işletim sistemlerinin farklılığının yanı sıra .NET Framework ile .NET 5 arasındaki farklılıklar söz konusu olduğunda, kullanmakta olduğunuz çerçeveye bağlı olarak belirli bir işletim sistemini ve belirli sürümleri hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="dafbd-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET 5, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="dafbd-105">Windows için Windows Server Core veya Windows nano Server kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbd-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="dafbd-106">Bu Windows sürümleri, sırasıyla .NET Framework veya .NET 5 tarafından gerekebilecek, farklı Özellikler (Windows Server Core 'ta IIS, Kestrel gibi şirket içinde barındırılan bir Web sunucusu) sağlar.</span><span class="sxs-lookup"><span data-stu-id="dafbd-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET 5, respectively.</span></span>

<span data-ttu-id="dafbd-107">Linux için, resmi .NET Docker görüntülerinde (Deklik gibi) Çoklu destekler mevcuttur ve desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dafbd-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="dafbd-108">Şekil 3-1 ' de, kullanılan .NET Framework 'e bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbd-108">In Figure 3-1, you can see the possible OS version depending on the .NET framework used.</span></span>

![Hangi .NET kapsayıcılarıyla kullanılacak işletim sistemini gösteren diyagram.](./media/net-container-os-targets/targeting-operating-systems.png)

<span data-ttu-id="dafbd-110">**Şekil 3-1.**</span><span class="sxs-lookup"><span data-stu-id="dafbd-110">**Figure 3-1.**</span></span> <span data-ttu-id="dafbd-111">.NET Framework sürümüne bağlı olarak hedeflenecek işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="dafbd-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="dafbd-112">Eski .NET Framework uygulamalar dağıtıldığında, eski uygulamalarla ve IIS ile uyumlu olan Windows Server çekirdeğini hedeflemek gerekir, ancak daha büyük bir görüntü içerir.</span><span class="sxs-lookup"><span data-stu-id="dafbd-112">When deploying legacy .NET Framework applications you have to target Windows Server Core, compatible with legacy apps and IIS, but it has a larger image.</span></span> <span data-ttu-id="dafbd-113">.NET 5 uygulamaları dağıttığınızda, buluta iyileştirilmiş Windows nano Server 'ı hedefleyebilir, Kestrel kullanır ve daha hızlı başlar.</span><span class="sxs-lookup"><span data-stu-id="dafbd-113">When deploying .NET 5 applications, you can target Windows Nano Server, which is cloud optimized, uses Kestrel and is smaller and starts faster.</span></span> <span data-ttu-id="dafbd-114">Ayrıca, Linux 'u destekleyebilir, alçam ve diğerlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbd-114">You can also target Linux, supporting Debian, Alpine, and others.</span></span> <span data-ttu-id="dafbd-115">Ayrıca, Kestrel kullanır, daha küçüktür ve daha hızlı başlar.</span><span class="sxs-lookup"><span data-stu-id="dafbd-115">Also uses Kestrel, is smaller, and starts faster.</span></span>

<span data-ttu-id="dafbd-116">Ayrıca, farklı bir Linux veya Microsoft tarafından sağlanmayan sürümlere sahip bir görüntü istediğiniz durumlarda kendi Docker görüntünüzü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbd-116">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="dafbd-117">Örneğin, Docker için olmayan-yaygın bir senaryo olan geleneksel .NET Framework ve Windows Server Core üzerinde çalışan ASP.NET Core bir görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbd-117">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dafbd-118">Windows Server çekirdek görüntülerini kullanırken, tam Windows görüntüleriyle karşılaştırıldığında bazı dll 'Lerin eksik olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbd-118">When using Windows Server Core images, you might find that some DLLs are missing, when compared to full Windows images.</span></span> <span data-ttu-id="dafbd-119">Bu sorunu, bu [GitHub açıklamasında](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)belirtildiği gibi, görüntü derleme zamanında eksik dosyaları ekleyerek özel bir sunucu çekirdeği görüntüsü oluşturarak çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbd-119">You might be able to solve this problem by creating a custom Server Core image, adding the missing files at image build time, as mentioned in this [GitHub comment](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).</span></span>

<span data-ttu-id="dafbd-120">Resim adını Dockerfile dosyanıza eklediğinizde, aşağıdaki örneklerde olduğu gibi, kullandığınız etikete bağlı olarak işletim sistemini ve sürümü seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dafbd-120">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

| <span data-ttu-id="dafbd-121">Görüntü</span><span class="sxs-lookup"><span data-stu-id="dafbd-121">Image</span></span> | <span data-ttu-id="dafbd-122">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="dafbd-122">Comments</span></span> |
|-------|----------|
| <span data-ttu-id="dafbd-123">mcr.microsoft.com/dotnet/runtime:5.0</span><span class="sxs-lookup"><span data-stu-id="dafbd-123">mcr.microsoft.com/dotnet/runtime:5.0</span></span> | <span data-ttu-id="dafbd-124">.NET 5 çoklu mimari: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler.</span><span class="sxs-lookup"><span data-stu-id="dafbd-124">.NET 5 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> |
| <span data-ttu-id="dafbd-125">mcr.microsoft.com/dotnet/aspnet:5.0</span><span class="sxs-lookup"><span data-stu-id="dafbd-125">mcr.microsoft.com/dotnet/aspnet:5.0</span></span> | <span data-ttu-id="dafbd-126">ASP.NET Core 5,0 Multi-Architecture: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler.</span><span class="sxs-lookup"><span data-stu-id="dafbd-126">ASP.NET Core 5.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> <br/> <span data-ttu-id="dafbd-127">Aspnetcore görüntüsünün ASP.NET Core için birkaç iyileştirmesi vardır.</span><span class="sxs-lookup"><span data-stu-id="dafbd-127">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span> |
| <span data-ttu-id="dafbd-128">mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim</span><span class="sxs-lookup"><span data-stu-id="dafbd-128">mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim</span></span> | <span data-ttu-id="dafbd-129">.NET 5 çalışma zamanı-yalnızca Linux 'ta Delinde</span><span class="sxs-lookup"><span data-stu-id="dafbd-129">.NET 5 runtime-only on Linux Debian distro</span></span> |
| <span data-ttu-id="dafbd-130">mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809</span><span class="sxs-lookup"><span data-stu-id="dafbd-130">mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809</span></span> | <span data-ttu-id="dafbd-131">.NET 5 çalışma zamanı-yalnızca Windows nano Server 'da (Windows Server sürüm 1809)</span><span class="sxs-lookup"><span data-stu-id="dafbd-131">.NET 5 runtime-only on Windows Nano Server (Windows Server version 1809)</span></span> |

## <a name="additional-resources"></a><span data-ttu-id="dafbd-132">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="dafbd-132">Additional resources</span></span>

- <span data-ttu-id="dafbd-133">**WindowsCodecsExt.dll eksik olması nedeniyle BitmapDecoder hata (GitHub sorunu)**</span><span class="sxs-lookup"><span data-stu-id="dafbd-133">**BitmapDecoder fails due to missing WindowsCodecsExt.dll (GitHub issue)**</span></span>  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> <span data-ttu-id="dafbd-134">[Önceki](container-framework-choice-factors.md) 
>  [Sonraki](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="dafbd-134">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
