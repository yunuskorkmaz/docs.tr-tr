---
title: Kapsayıcılar ve Docker giriş
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Kapsayıcılar ve Docker giriş
keywords: Docker, mikro, ASP.NET, kapsayıcı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8809ae41609ff0e2d2fc969d412cb5edc8939653
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="a9e86-104">Kapsayıcılar ve Docker giriş</span><span class="sxs-lookup"><span data-stu-id="a9e86-104">Introduction to Containers and Docker</span></span>

<span data-ttu-id="a9e86-105">Kapsayıcıyla taşıma, bir uygulama veya hizmet, bağımlılıklarını ve (dağıtım bildirim dosyaları olarak soyutlanır) yapılandırmasıyla birlikte bir kapsayıcı görüntüsü olarak paketlenmiş yazılım geliştirme için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="a9e86-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="a9e86-106">Kapsayıcılı uygulama bir birim olarak test ve ana bilgisayar işletim sistemi (OS) için bir kapsayıcı görüntü örneği olarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="a9e86-106">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="a9e86-107">Yalnızca sevkiyat kapsayıcıları gemi, tren veya kamyon içinde Kargo bakılmaksızın tarafından taşınmasını mal izin olarak yazılım kapsayıcıları farklı kodu ve bağımlılıklarını içeren bir yazılım standart birimi olarak hareket.</span><span class="sxs-lookup"><span data-stu-id="a9e86-107">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="a9e86-108">Bu şekilde yazılım containerizing, geliştiriciler ve BT uzmanları bunları çok az kayıpla veya hiç değişiklik ortamlarıyla üzerinden dağıtmak etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a9e86-108">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="a9e86-109">Kapsayıcılar ayrıca birbirinden uygulamalar, paylaşılan bir işletim sistemine yalıtma.</span><span class="sxs-lookup"><span data-stu-id="a9e86-109">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="a9e86-110">Kapsayıcılı uygulamaları sırayla işletim sisteminde (Linux veya Windows) çalıştıran bir kapsayıcı konak üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="a9e86-110">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="a9e86-111">Kapsayıcılar, bu nedenle sanal makine (VM) görüntüleri daha önemli ölçüde daha küçük bir yer gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9e86-111">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="a9e86-112">Her kapsayıcı, Şekil 2-1'de gösterildiği gibi tüm web uygulaması veya bir hizmet çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e86-112">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="a9e86-113">Bu örnekte, Docker ana bir kapsayıcı konak ve App1 ve App2, Svc 1 ve Svc 2 kapsayıcılı uygulamalar veya hizmetler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="a9e86-113">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![](./media/image1.png)

<span data-ttu-id="a9e86-114">**Şekil 2-1**.</span><span class="sxs-lookup"><span data-stu-id="a9e86-114">**Figure 2-1**.</span></span> <span data-ttu-id="a9e86-115">Bir kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="a9e86-115">Multiple containers running on a container host</span></span>

<span data-ttu-id="a9e86-116">Kapsayıcıyla taşıma başka bir yararı ölçeklenebilirlik özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="a9e86-116">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="a9e86-117">Out hızlı bir şekilde kısa vadeli görevler için yeni kapsayıcılar oluşturarak ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e86-117">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="a9e86-118">Bir uygulama açısından bakıldığında, (bir kapsayıcı oluşturma) bir görüntü örneği bir hizmet veya web uygulaması gibi bir işlem örneği için benzer.</span><span class="sxs-lookup"><span data-stu-id="a9e86-118">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="a9e86-119">Birden çok ana bilgisayar sunucuları arasında aynı görüntü birden çok örneğini çalıştırdığınızda güvenilirliği, ancak genellikle her kapsayıcı (bir farklı ana bilgisayar sunucusu çalıştırmak için görüntü örneği) veya VM farklı hata etki alanlarında istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e86-119">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="a9e86-120">Kısacası, kapsayıcıları tüm uygulama yaşam döngüsü iş akışı yalıtımı, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetim avantajları sunar.</span><span class="sxs-lookup"><span data-stu-id="a9e86-120">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="a9e86-121">En önemli avantajı geliştirme ve Ops arasında sağlanan yalıtım ' dir.</span><span class="sxs-lookup"><span data-stu-id="a9e86-121">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a9e86-122">[Önceki] (.. / index.md) [sonraki] (docker-defined.md)</span><span class="sxs-lookup"><span data-stu-id="a9e86-122">[Previous] (../index.md) [Next] (docker-defined.md)</span></span>
