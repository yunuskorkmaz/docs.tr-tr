---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Kayıt defterleri uygulamaları dağıtma Docker şekilde genel play önemli bir rol öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641341"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="b955f-103">Docker kapsayıcıları, görüntüleri ve kayıt defterleri</span><span class="sxs-lookup"><span data-stu-id="b955f-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="b955f-104">Docker'ı kullanarak bir uygulama veya hizmeti ve paketi ve bağımlılıkları bir kapsayıcı görüntüsü oluşturduğunuzda.</span><span class="sxs-lookup"><span data-stu-id="b955f-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="b955f-105">Görüntü uygulamayı veya hizmeti ve kendi yapılandırma ve bağımlılıklarla statik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="b955f-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="b955f-106">Uygulamanızı veya hizmetinizi çalıştırmak için uygulamanın resmi Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b955f-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="b955f-107">Kapsayıcı başlangıçta bir geliştirme ortamı veya bilgisayar test edilmez.</span><span class="sxs-lookup"><span data-stu-id="b955f-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="b955f-108">Görüntü kitaplığı davranan bir kayıt defteri, görüntüleri depolayın.</span><span class="sxs-lookup"><span data-stu-id="b955f-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="b955f-109">Bir kayıt defteri için üretim düzenleyicileri dağıtırken gerekir.</span><span class="sxs-lookup"><span data-stu-id="b955f-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="b955f-110">Genel bir kayıt defterinden docker tutar [Docker Hub](https://hub.docker.com/); diğer satıcıları görüntüleri dahil olmak üzere, farklı koleksiyonlar için kayıt defterleri sağlayan [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="b955f-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="b955f-111">Alternatif olarak, kuruluşlar, özel bir kayıt defteri sahip olabilir, kendi Docker görüntüleri için şirket içi.</span><span class="sxs-lookup"><span data-stu-id="b955f-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="b955f-112">Şekil 1-4 nasıl görüntüler ve Docker kayıt defterleri için diğer bileşenleri ilişkilendirilmesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b955f-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="b955f-113">Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.</span><span class="sxs-lookup"><span data-stu-id="b955f-113">It also shows the multiple registry offerings from vendors.</span></span>

![Docker temel taksonomisinde: Kayıt defteri, görüntüleri depolanan ve hizmeti veya web uygulaması çalıştırmak için kapsayıcılar oluşturmak için çekilmesi kullanılabilir olduğu gibi bir bookshelf olduğu.](./media/image4.png)

<span data-ttu-id="b955f-118">**Şekil 1-4**.</span><span class="sxs-lookup"><span data-stu-id="b955f-118">**Figure 1-4**.</span></span> <span data-ttu-id="b955f-119">Docker terimleri ve kavramları'nin Taksonomisi</span><span class="sxs-lookup"><span data-stu-id="b955f-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="b955f-120">Kayıt defterindeki görüntüleri koyarak çerçevesi düzeyinde, bağımlılıklarının tümü de dahil olmak üzere, statik ve sabit uygulama BITS depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b955f-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="b955f-121">Ardından sürüm ve birden çok ortama görüntülerde dağıtabilir ve bu nedenle, tutarlı dağıtım birimi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="b955f-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="b955f-122">Özel görüntü kayıt defterleri, barındırılan şirket içinde veya bulutta, ne zaman önerilir:</span><span class="sxs-lookup"><span data-stu-id="b955f-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="b955f-123">Nedeniyle gizlilik görüntülerinizin herkese açık şekilde paylaşılmamalı.</span><span class="sxs-lookup"><span data-stu-id="b955f-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="b955f-124">Görüntüleri ve seçilen dağıtım ortamınız arasında düşük ağ gecikme süresine sahiptir istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b955f-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="b955f-125">Üretim ortamınızı Azure ise, örneğin, büyük olasılıkla görüntülerinizi depolamak istediğiniz [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) ağ gecikme süresi çok az olmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="b955f-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="b955f-126">Üretim ortamınıza şirket içinde ise benzer şekilde, bu, bir şirket içi Docker Trusted Registry aynı yerel ağda kullanılabilir olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b955f-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b955f-127">[Önceki](docker-terminology.md)
>[İleri](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="b955f-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
