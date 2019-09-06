---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Docker kapsayıcıları, görüntüleri ve kayıt defterleri
ms.date: 08/31/2018
ms.openlocfilehash: 520f8d4d54f1fdd227ff9a1e88660b62e75f927f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296201"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="53c66-103">Docker kapsayıcıları, görüntüleri ve kayıt defterleri</span><span class="sxs-lookup"><span data-stu-id="53c66-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="53c66-104">Bir geliştirici, Docker kullanırken bir uygulama veya hizmet oluşturur ve onun bağımlılıklarını ve onun bağımlılıklarını bir kapsayıcı görüntüsüne paketler.</span><span class="sxs-lookup"><span data-stu-id="53c66-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="53c66-105">Görüntü, uygulamanın veya hizmetin statik bir gösterimidir ve yapılandırma ve bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="53c66-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="53c66-106">Uygulamayı veya hizmeti çalıştırmak için, uygulamanın görüntüsü, Docker konağında çalışacak bir kapsayıcı oluşturmak için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53c66-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="53c66-107">Kapsayıcılar başlangıçta bir geliştirme ortamında veya bılgısayarda test edilir.</span><span class="sxs-lookup"><span data-stu-id="53c66-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="53c66-108">Geliştiriciler görüntüleri bir kayıt defteri halinde depolamalıdır ve bu, görüntü kitaplığı gibi davranır ve üretim düzenleyicilerine dağıtıldığında gereklidir.</span><span class="sxs-lookup"><span data-stu-id="53c66-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="53c66-109">Docker, [Docker Hub](https://hub.docker.com/)aracılığıyla ortak bir kayıt defteri sağlar; diğer satıcılar, [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)dahil olmak üzere farklı görüntü koleksiyonlarına yönelik kayıt defterleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="53c66-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="53c66-110">Alternatif olarak, kuruluşlar kendi Docker görüntüleri için şirket içinde özel bir kayıt defterine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="53c66-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="53c66-111">Şekil 2-4, Docker 'daki görüntülerin ve kayıt defterlerinin diğer bileşenlerle nasıl ilişkisi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="53c66-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="53c66-112">Ayrıca, satıcıların birden çok kayıt defteri teklifini gösterir.</span><span class="sxs-lookup"><span data-stu-id="53c66-112">It also shows the multiple registry offerings from vendors.</span></span>

![Docker 'da temel taksonomi: Kayıt defteri, görüntülerin depolandığı ve hizmetleri ya da Web Apps 'i çalıştırmak üzere kapsayıcılar oluşturmak için çekilmek üzere kullanılabilecek bir Bookshelf gibidir.](./media/image5.PNG)

<span data-ttu-id="53c66-117">**Şekil 2-4**.</span><span class="sxs-lookup"><span data-stu-id="53c66-117">**Figure 2-4**.</span></span> <span data-ttu-id="53c66-118">Docker hüküm ve kavramlarının sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="53c66-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="53c66-119">Görüntüleri bir kayıt defterine koymak, tüm bağımlılıkları dahil olmak üzere statik ve değişmez uygulama bitlerini bir çerçeve düzeyinde depolamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="53c66-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="53c66-120">Bu görüntüler daha sonra birden fazla ortamda sürümlenebilir ve dağıtılabilir ve bu nedenle tutarlı bir dağıtım birimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="53c66-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="53c66-121">Şirket içinde veya bulutta barındırılan özel görüntü kayıt defterleri şu durumlarda önerilir:</span><span class="sxs-lookup"><span data-stu-id="53c66-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="53c66-122">Gizli olmaması nedeniyle görüntülerinizin genel olarak paylaşılmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="53c66-122">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="53c66-123">Resimleriniz ve seçtiğiniz dağıtım ortamınız arasında en düşük ağ gecikme süresine sahip olmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="53c66-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="53c66-124">Örneğin, üretim ortamınız Azure bulutunuz ise, büyük ihtimalle, ağ gecikmesi en düşük olacak şekilde [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) görüntülerini depolamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53c66-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="53c66-125">Benzer bir şekilde, üretim ortamınız şirket içindeyse, aynı yerel ağ içinde şirket içi bir Docker güvenilir kayıt defteri kullanılabilir olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53c66-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="53c66-126">[Önceki](docker-terminology.md)İleri
>[](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="53c66-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>
