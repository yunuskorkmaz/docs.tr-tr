---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker kapsayıcıları, görüntüleri ve kayıt defterleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 1ab5f2f4172caf799b9a63c1ae881a66f8805e20
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659653"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="f3578-103">Docker kapsayıcıları, görüntüleri ve kayıt defterleri</span><span class="sxs-lookup"><span data-stu-id="f3578-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="f3578-104">Docker'ı kullanarak, bir geliştirici bir uygulama veya hizmet ve paketleri ve bağımlılıklarını kapsayıcı görüntüsüne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3578-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="f3578-105">Görüntü uygulamayı veya hizmeti ve kendi yapılandırma ve bağımlılıklarla statik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="f3578-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="f3578-106">Uygulamanızı veya hizmetinizi çalıştırmak için uygulamanın resmi Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f3578-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="f3578-107">Kapsayıcı başlangıçta bir geliştirme ortamı veya bilgisayar test edilmez.</span><span class="sxs-lookup"><span data-stu-id="f3578-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="f3578-108">Geliştiriciler, bir görüntü kitaplığı olarak davranır ve üretim düzenleyiciler için dağıtırken gereken bir kayıt defteri görüntüleri depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3578-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="f3578-109">Genel bir kayıt defterinden docker tutar [Docker Hub](https://hub.docker.com/); diğer satıcıları görüntüleri dahil olmak üzere, farklı koleksiyonlar için kayıt defterleri sağlayan [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="f3578-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="f3578-110">Alternatif olarak, kuruluşlar, özel bir kayıt defteri sahip olabilir, kendi Docker görüntüleri için şirket içi.</span><span class="sxs-lookup"><span data-stu-id="f3578-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="f3578-111">Şekil 2-4 nasıl görüntüler ve Docker kayıt defterleri için diğer bileşenleri ilişkilendirilmesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3578-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="f3578-112">Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3578-112">It also shows the multiple registry offerings from vendors.</span></span>

![Docker temel taksonomisinde: Kayıt defteri, görüntüleri depolanan ve hizmeti veya web uygulaması çalıştırmak için kapsayıcılar oluşturmak için çekilmesi kullanılabilir olduğu gibi bir bookshelf olduğu.](./media/image5.PNG)

<span data-ttu-id="f3578-117">**Şekil 2-4**.</span><span class="sxs-lookup"><span data-stu-id="f3578-117">**Figure 2-4**.</span></span> <span data-ttu-id="f3578-118">Docker terimleri ve kavramları'nin Taksonomisi</span><span class="sxs-lookup"><span data-stu-id="f3578-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="f3578-119">Kayıt defterindeki görüntüleri yerleştirme çerçevesi düzeyinde, tüm bağımlılıklar dahil olmak üzere, statik ve sabit uygulama BITS depolamanıza olanak tanıyan.</span><span class="sxs-lookup"><span data-stu-id="f3578-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="f3578-120">Bu görüntüleri, ardından oluşturulan ve dağıtılan birden çok ortamda ve bu nedenle, tutarlı dağıtım birimi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f3578-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="f3578-121">Özel görüntü kayıt defterleri, barındırılan şirket içinde veya bulutta, ne zaman önerilir:</span><span class="sxs-lookup"><span data-stu-id="f3578-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="f3578-122">Nedeniyle gizlilik görüntülerinizin herkese açık şekilde paylaşılmamalı.</span><span class="sxs-lookup"><span data-stu-id="f3578-122">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="f3578-123">Görüntüleri ve seçilen dağıtım ortamınız arasında düşük ağ gecikme süresine sahiptir istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f3578-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="f3578-124">Üretim ortamınızı Azure bulut ise, örneğin, büyük olasılıkla görüntülerinizi depolamak istediğiniz [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) ağ gecikme süresi çok az olması.</span><span class="sxs-lookup"><span data-stu-id="f3578-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="f3578-125">Üretim ortamınıza şirket içinde ise benzer şekilde, bu, bir şirket içi Docker Trusted Registry aynı yerel ağda kullanılabilir olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3578-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f3578-126">[Önceki](docker-terminology.md)
>[İleri](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="f3578-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>