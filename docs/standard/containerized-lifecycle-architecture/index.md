---
title: Kapsayıcılar ve Docker giriş
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: e9f81c5fecc06b19ebd84cc4b2cc232686768a90
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106638"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="cfb53-103">Kapsayıcılar ve Docker giriş</span><span class="sxs-lookup"><span data-stu-id="cfb53-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="cfb53-104">Kapsayıcıyla taşıma, bir uygulama veya hizmet, bağımlılıklarını ve (dağıtım bildirim dosyaları olarak soyutlanır) yapılandırmasıyla birlikte bir kapsayıcı görüntüsü olarak paketlenmiş yazılım geliştirme için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="cfb53-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="cfb53-105">Ardından bir birim olarak kapsayıcılı uygulamayı test etme ve ana bilgisayar işletim sistemi için bir kapsayıcı görüntü örneği olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfb53-105">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="cfb53-106">Yalnızca sevk, tren veya bunları içinde Kargo bakılmaksızın kamyon mal taşımak için standartlaştırılmış kapsayıcıları sevkiyat endüstri kullanır gibi yazılım kapsayıcıları farklı kodu ve bağımlılıklarını içeren bir yazılım standart birimi davranır.</span><span class="sxs-lookup"><span data-stu-id="cfb53-106">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="cfb53-107">Yazılım kapsayıcılarına yerleştirme, geliştiriciler ve BT Uzmanları bu kapsayıcıların çok az kayıpla veya hiç değişiklik ortamlarıyla üzerinden dağıtmak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="cfb53-107">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="cfb53-108">Kapsayıcılar ayrıca paylaşılan bir işletim sistemine (OS) uygulamaları birbirinden yalıtmak.</span><span class="sxs-lookup"><span data-stu-id="cfb53-108">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="cfb53-109">Kapsayıcılı uygulamaları sırayla (Linux veya Windows) işletim sisteminde çalışan bir kapsayıcı konak üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="cfb53-109">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="cfb53-110">Bu nedenle, sanal makine (VM) görüntüleri daha önemli ölçüde daha küçük bir yer kapsayıcıları sahip.</span><span class="sxs-lookup"><span data-stu-id="cfb53-110">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="cfb53-111">Her bir kapsayıcıdaki tüm web uygulaması veya hizmeti, Şekil 1-1'de gösterildiği gibi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfb53-111">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="cfb53-112">Şekil 1-1: bir kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="cfb53-112">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="cfb53-113">Bu örnekte, Docker ana kapsayıcı ana bilgisayar ve uygulama, uygulama 2, Svc 1, Svc 2 kapsayıcılı uygulamalar veya hizmetler şunlardır: 1 ve.</span><span class="sxs-lookup"><span data-stu-id="cfb53-113">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="cfb53-114">Kapsayıcıyla taşıma türetilen başka bir avantaj ölçeklenebilirlik olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cfb53-114">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="cfb53-115">Hızlı bir şekilde kısa vadeli görevler için yeni kapsayıcılar oluşturarak genişletme.</span><span class="sxs-lookup"><span data-stu-id="cfb53-115">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="cfb53-116">Açısından bir uygulama, *görüntü başlatmasını* (bir kapsayıcı oluşturma) benzer bir hizmeti veya web uygulaması gibi bir işlem örneği için.</span><span class="sxs-lookup"><span data-stu-id="cfb53-116">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="cfb53-117">Birden çok ana bilgisayar sunucuları arasında aynı görüntü birden çok örneğini çalıştırdığınızda güvenilirliği, ancak genellikle her kapsayıcı (bir farklı ana bilgisayar sunucusu çalıştırmak için görüntü örneği) veya VM farklı hata etki alanlarında istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="cfb53-117">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="cfb53-118">Kısacası, kapsayıcıları tüm uygulama yaşam döngüsü iş akışı yalıtımı, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetim avantajları sunar.</span><span class="sxs-lookup"><span data-stu-id="cfb53-118">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="cfb53-119">En önemli avantajı geliştirme ve Ops arasında sağlanan yalıtım ' dir.</span><span class="sxs-lookup"><span data-stu-id="cfb53-119">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
[<span data-ttu-id="cfb53-120">Next</span><span class="sxs-lookup"><span data-stu-id="cfb53-120">Next</span></span>](what-is-docker.md)
