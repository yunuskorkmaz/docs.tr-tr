---
title: Docker kapsayıcıları, görüntüler ve kayıt defterleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Docker kapsayıcıları, görüntüler ve kayıt defterleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 4716159d052fd8e229ac42e5d17c72717ac86d9f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106466"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="1ab03-103">Docker kapsayıcıları, görüntüler ve kayıt defterleri</span><span class="sxs-lookup"><span data-stu-id="1ab03-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="1ab03-104">Docker kullanırken, bir geliştirici bir uygulama veya hizmet ve paketleri ve bağımlılıklarını kapsayıcı görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ab03-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="1ab03-105">Görüntü uygulama veya hizmet ve yapılandırma ve bağımlılıkları statik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="1ab03-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="1ab03-106">Uygulama veya hizmeti çalıştırmak için uygulamanın görüntü Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği.</span><span class="sxs-lookup"><span data-stu-id="1ab03-106">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="1ab03-107">Kapsayıcılar, başlangıçta bir geliştirme ortamı veya PC sınanır.</span><span class="sxs-lookup"><span data-stu-id="1ab03-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="1ab03-108">Geliştiricilerin görüntüleri görüntülerinin kitaplık olarak davranır ve üretim orchestrators dağıtırken gereken bir kayıt defteri depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ab03-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="1ab03-109">Docker tutar ortak kayıt defterinden [Docker hub'a](https://hub.docker.com/); diğer satıcılar görüntüleri farklı koleksiyonlar için kayıt defterleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="1ab03-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="1ab03-110">Alternatif olarak, kuruluşların özel bir kayıt defteri olabilir şirket içi kendi Docker görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ab03-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="1ab03-111">Şekil 2-4 ne görüntüleri ve kayıt defterleri Docker içindeki diğer bileşenlere ilişkili gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ab03-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="1ab03-112">Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ab03-112">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="1ab03-113">**Şekil 2-4**.</span><span class="sxs-lookup"><span data-stu-id="1ab03-113">**Figure 2-4**.</span></span> <span data-ttu-id="1ab03-114">Sınıflandırma Docker terimleri ve kavramları</span><span class="sxs-lookup"><span data-stu-id="1ab03-114">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="1ab03-115">Kayıt defterinde görüntüleri koyma framework düzeydeki tüm bağımlılıklarını dahil olmak üzere sabit ve değişmez uygulama BITS depolamak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ab03-115">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="1ab03-116">Bu görüntüleri sürümlü hem de birden çok ortamlarda dağıtılan ve bu nedenle tutarlı bir dağıtım birimi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="1ab03-116">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="1ab03-117">Özel görüntü kayıt defterleri, barındırılan şirket içi veya bulutta ne zaman önerilir:</span><span class="sxs-lookup"><span data-stu-id="1ab03-117">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="1ab03-118">Görüntülerinizi herkese açık şekilde nedeniyle gizliliği paylaşılması değil.</span><span class="sxs-lookup"><span data-stu-id="1ab03-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="1ab03-119">Görüntülerinizi seçilen dağıtım ortamınızı arasındaki en düşük ağ gecikmesini olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="1ab03-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="1ab03-120">Üretim ortamınıza Azure bulut ise, örneğin, büyük olasılıkla ağ gecikme süresi en az olması görüntülerinizi Azure kapsayıcı kayıt defterine depolamak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="1ab03-120">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="1ab03-121">Üretim ortamınıza şirket ise benzer şekilde, bir şirket içi Docker güvenilen kayıt defteri aynı yerel ağ içinde kullanılabilir olmasını istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="1ab03-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="1ab03-122">[Önceki](docker-terminology.md)
[sonraki](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="1ab03-122">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>
