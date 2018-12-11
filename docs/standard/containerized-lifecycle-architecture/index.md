---
title: Kapsayıcılar ve Docker'a giriş
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: c2a6b9802bbb995939d33c5c40ef9c1afa1620e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148827"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="eb306-103">Kapsayıcılar ve Docker'a giriş</span><span class="sxs-lookup"><span data-stu-id="eb306-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="eb306-104">Kapsayıcı içinde bir uygulama veya hizmeti ve bağımlılıklarını yapılandırmasıyla (dağıtım bildirim dosyaları soyutlanır) bir arada bir kapsayıcı görüntüsü paketlenmiş yazılım geliştirme için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="eb306-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="eb306-105">Daha sonra bir birim olarak kapsayıcılı uygulamayı test etme ve bir kapsayıcı görüntü örneğinin konak işletim sistemi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb306-105">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="eb306-106">Yalnızca ürün sevk, train veya kargo içindeki ne olursa olsun, kamyon taşımak için standartlaştırılmış kapsayıcıları sevkiyat sektör kullandığı yazılım kapsayıcıları farklı kodu ve bağımlılıkları içeren bir yazılım standart birimi davranır.</span><span class="sxs-lookup"><span data-stu-id="eb306-106">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="eb306-107">Yazılım kapsayıcılarına yerleştirme ortamlarında çok az kayıpla veya hiç değişiklik ile Bu kapsayıcıları dağıtmak, geliştiriciler ve BT uzmanları için mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="eb306-107">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="eb306-108">Kapsayıcılar Ayrıca, paylaşılan bir işletim sistemi (OS) uygulamaları birbirinden yalıtın.</span><span class="sxs-lookup"><span data-stu-id="eb306-108">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="eb306-109">Kapsayıcılı uygulamaların, işletim sisteminde (Linux veya Windows) sırayla çalışır bir kapsayıcı konağı üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb306-109">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="eb306-110">Bu nedenle, kapsayıcılar, sanal makine (VM) görüntülerini daha önemli ölçüde daha küçük bir ayak izini içerir.</span><span class="sxs-lookup"><span data-stu-id="eb306-110">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="eb306-111">Her kapsayıcı, tüm web uygulaması veya hizmeti, Şekil 1-1'de gösterildiği gibi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb306-111">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="eb306-112">Şekil 1-1: Bir kapsayıcı konağı üzerinde çalışan birden çok kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="eb306-112">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="eb306-113">Bu örnekte, Docker ana bir kapsayıcı konağı ve kapsayıcılı uygulamalar veya hizmetler uygulama 1, uygulama 2, Svc'de 1 ve Svc 2'dir.</span><span class="sxs-lookup"><span data-stu-id="eb306-113">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="eb306-114">Kapsayıcı türetilip bir diğer avantajı ölçeklenebilirlik özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="eb306-114">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="eb306-115">Hızla yeni kapsayıcılar için kısa vadeli görevleri oluşturarak ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="eb306-115">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="eb306-116">Bir uygulama açısından, *görüntü örnekleme* (bir kapsayıcı oluşturma), bir hizmeti veya web uygulaması gibi bir işlem örnekleme için benzerdir.</span><span class="sxs-lookup"><span data-stu-id="eb306-116">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="eb306-117">Birden çok ana bilgisayar sunucuları arasında aynı görüntüsünün birden çok örneği çalıştırdığınızda güvenilirliği, ancak genellikle her bir kapsayıcı (farklı bir ana sunucu çalıştırmak için görüntü örnek) veya VM farklı hata etki alanlarında istersiniz.</span><span class="sxs-lookup"><span data-stu-id="eb306-117">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="eb306-118">Kısacası, kapsayıcılar arasında tüm uygulama yaşam döngüsü iş akışı yalıtımı, taşınabilirliği, çevikliği, ölçeklenebilirlik ve denetim avantajlarını sunar.</span><span class="sxs-lookup"><span data-stu-id="eb306-118">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="eb306-119">En önemli avantajı, geliştirme ve Ops sağlanan yalıtım içindir.</span><span class="sxs-lookup"><span data-stu-id="eb306-119">The most important benefit is the isolation provided between Dev and Ops.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="eb306-120">Next</span><span class="sxs-lookup"><span data-stu-id="eb306-120">Next</span></span>](what-is-docker.md)