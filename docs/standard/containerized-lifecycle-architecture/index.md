---
title: "Kapsayıcılar ve Docker giriş"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 31260dc372f87305ad9d4556673a1cc94e24bfcc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="21b30-104">Kapsayıcılar ve Docker giriş</span><span class="sxs-lookup"><span data-stu-id="21b30-104">Introduction to containers and Docker</span></span>

<span data-ttu-id="21b30-105">Kapsayıcıyla taşıma, bir uygulama veya hizmet, bağımlılıklarını ve (dağıtım bildirim dosyaları olarak soyutlanır) yapılandırmasıyla birlikte bir kapsayıcı görüntüsü olarak paketlenmiş yazılım geliştirme için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="21b30-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="21b30-106">Ardından bir birim olarak kapsayıcılı uygulamayı test etme ve ana bilgisayar işletim sistemi için bir kapsayıcı görüntü örneği olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21b30-106">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="21b30-107">Yalnızca sevk, tren veya bunları içinde Kargo bakılmaksızın kamyon mal taşımak için standartlaştırılmış kapsayıcıları sevkiyat endüstri kullanır gibi yazılım kapsayıcıları farklı kodu ve bağımlılıklarını içeren bir yazılım standart birimi davranır.</span><span class="sxs-lookup"><span data-stu-id="21b30-107">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="21b30-108">Yazılım kapsayıcılarına yerleştirme, geliştiriciler ve BT Uzmanları bu kapsayıcıların çok az kayıpla veya hiç değişiklik ortamlarıyla üzerinden dağıtmak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="21b30-108">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="21b30-109">Kapsayıcılar ayrıca paylaşılan bir işletim sistemine (OS) uygulamaları birbirinden yalıtmak.</span><span class="sxs-lookup"><span data-stu-id="21b30-109">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="21b30-110">Kapsayıcılı uygulamaları sırayla (Linux veya Windows) işletim sisteminde çalışan bir kapsayıcı konak üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="21b30-110">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="21b30-111">Bu nedenle, sanal makine (VM) görüntüleri daha önemli ölçüde daha küçük bir yer kapsayıcıları sahip.</span><span class="sxs-lookup"><span data-stu-id="21b30-111">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="21b30-112">Her bir kapsayıcıdaki tüm web uygulaması veya hizmeti, Şekil 1-1'de gösterildiği gibi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21b30-112">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="21b30-113">Şekil 1-1: bir kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="21b30-113">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="21b30-114">Bu örnekte, Docker ana kapsayıcı ana bilgisayar ve uygulama, uygulama 2, Svc 1, Svc 2 kapsayıcılı uygulamalar veya hizmetler şunlardır: 1 ve.</span><span class="sxs-lookup"><span data-stu-id="21b30-114">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="21b30-115">Kapsayıcıyla taşıma türetilen başka bir avantaj ölçeklenebilirlik olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21b30-115">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="21b30-116">Hızlı bir şekilde kısa vadeli görevler için yeni kapsayıcılar oluşturarak genişletme.</span><span class="sxs-lookup"><span data-stu-id="21b30-116">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="21b30-117">Açısından bir uygulama, *görüntü başlatmasını* (bir kapsayıcı oluşturma) benzer bir hizmeti veya web uygulaması gibi bir işlem örneği için.</span><span class="sxs-lookup"><span data-stu-id="21b30-117">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="21b30-118">Birden çok ana bilgisayar sunucuları arasında aynı görüntü birden çok örneğini çalıştırdığınızda güvenilirliği, ancak genellikle her kapsayıcı (bir farklı ana bilgisayar sunucusu çalıştırmak için görüntü örneği) veya VM farklı hata etki alanlarında istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="21b30-118">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="21b30-119">Kısacası, kapsayıcıları tüm uygulama yaşam döngüsü iş akışı yalıtımı, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetim avantajları sunar.</span><span class="sxs-lookup"><span data-stu-id="21b30-119">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="21b30-120">En önemli avantajı geliştirme ve Ops arasında sağlanan yalıtım ' dir.</span><span class="sxs-lookup"><span data-stu-id="21b30-120">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="21b30-121">[Sonraki] (what-olduğu-docker.md)</span><span class="sxs-lookup"><span data-stu-id="21b30-121">[Next] (what-is-docker.md)</span></span>
