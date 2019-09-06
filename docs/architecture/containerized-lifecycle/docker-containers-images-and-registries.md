---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Kayıt defterlerinin, uygulamaları dağıtmanın Docker yolunda genel olarak oynamakta olduğu anahtar rolü öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295660"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="8e048-103">Docker kapsayıcıları, görüntüleri ve kayıt defterleri</span><span class="sxs-lookup"><span data-stu-id="8e048-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="8e048-104">Docker kullanırken bir uygulama veya hizmet oluşturur ve onun bağımlılıklarını bir kapsayıcı görüntüsüne paketleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8e048-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="8e048-105">Görüntü, uygulamanın veya hizmetin statik bir gösterimidir ve yapılandırma ve bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="8e048-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="8e048-106">Uygulamayı veya hizmeti çalıştırmak için, uygulamanın görüntüsü, Docker konağında çalışacak bir kapsayıcı oluşturmak için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8e048-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="8e048-107">Kapsayıcılar başlangıçta bir geliştirme ortamında veya bılgısayarda test edilir.</span><span class="sxs-lookup"><span data-stu-id="8e048-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="8e048-108">Görüntüleri bir görüntü kitaplığı gibi davranan bir kayıt defterine depoladığınızda.</span><span class="sxs-lookup"><span data-stu-id="8e048-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="8e048-109">Üretim düzenleyicilerine dağıtım yaparken bir kayıt defteri gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e048-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="8e048-110">Docker, [Docker Hub](https://hub.docker.com/)aracılığıyla ortak bir kayıt defteri sağlar; diğer satıcılar, [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)dahil olmak üzere farklı görüntü koleksiyonlarına yönelik kayıt defterleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e048-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="8e048-111">Alternatif olarak, kuruluşlar kendi Docker görüntüleri için şirket içinde özel bir kayıt defterine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8e048-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="8e048-112">Şekil 1-4, Docker 'daki görüntülerin ve kayıt defterlerinin diğer bileşenlerle nasıl ilişkisi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e048-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="8e048-113">Ayrıca, satıcıların birden çok kayıt defteri teklifini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e048-113">It also shows the multiple registry offerings from vendors.</span></span>

![Docker 'da temel taksonomi: Kayıt defteri, görüntülerin depolandığı ve hizmetleri ya da Web Apps 'i çalıştırmak üzere kapsayıcılar oluşturmak için çekilmek üzere kullanılabilecek bir Bookshelf gibidir.](./media/image4.png)

<span data-ttu-id="8e048-118">**Şekil 1-4**.</span><span class="sxs-lookup"><span data-stu-id="8e048-118">**Figure 1-4**.</span></span> <span data-ttu-id="8e048-119">Docker hüküm ve kavramlarının sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="8e048-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="8e048-120">Görüntüleri bir kayıt defterine yerleştirerek, tüm bağımlılıkları dahil olmak üzere statik ve değişmez uygulama bitlerini bir çerçeve düzeyinde saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e048-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="8e048-121">Daha sonra görüntüleri birden çok ortamda dağıtıp dağıtabilir ve böylece tutarlı bir dağıtım birimi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e048-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="8e048-122">Şirket içinde veya bulutta barındırılan özel görüntü kayıt defterleri şu durumlarda önerilir:</span><span class="sxs-lookup"><span data-stu-id="8e048-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="8e048-123">Gizli olmaması nedeniyle görüntülerinizin genel olarak paylaşılmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e048-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="8e048-124">Resimleriniz ve seçtiğiniz dağıtım ortamınız arasında en düşük ağ gecikme süresine sahip olmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="8e048-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="8e048-125">Örneğin, üretim ortamınız Azure ise, büyük olasılıkla, ağ gecikmesi en düşük olması için görüntülerinizi [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) saklamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8e048-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="8e048-126">Benzer bir şekilde, üretim ortamınız şirket içindeyse, aynı yerel ağ içinde şirket içi bir Docker güvenilir kayıt defteri kullanılabilir olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e048-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8e048-127">[Önceki](docker-terminology.md)İleri
>[](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="8e048-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
