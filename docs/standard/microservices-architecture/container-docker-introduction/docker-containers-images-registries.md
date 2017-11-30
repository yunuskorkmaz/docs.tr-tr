---
title: "Docker kapsayıcıları, görüntüler ve kayıt defterleri"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Docker kapsayıcıları, görüntüler ve kayıt defterleri"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="e7078-104">Docker kapsayıcıları, görüntüler ve kayıt defterleri</span><span class="sxs-lookup"><span data-stu-id="e7078-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="e7078-105">Docker kullanırken, bir geliştirici bir uygulama veya hizmet ve paketleri ve bağımlılıklarını kapsayıcı görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e7078-105">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="e7078-106">Görüntü uygulama veya hizmet ve yapılandırma ve bağımlılıkları statik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="e7078-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="e7078-107">Uygulama veya hizmeti çalıştırmak için uygulamanın görüntü Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği.</span><span class="sxs-lookup"><span data-stu-id="e7078-107">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="e7078-108">Kapsayıcılar, başlangıçta bir geliştirme ortamı veya PC sınanır.</span><span class="sxs-lookup"><span data-stu-id="e7078-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="e7078-109">Geliştiricilerin görüntüleri görüntülerinin kitaplık olarak davranır ve üretim orchestrators dağıtırken gereken bir kayıt defteri depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7078-109">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="e7078-110">Docker tutar ortak kayıt defterinden [Docker hub'a](https://hub.docker.com/); diğer satıcılar görüntüleri farklı koleksiyonlar için kayıt defterleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e7078-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="e7078-111">Alternatif olarak, kuruluşların özel bir kayıt defteri olabilir şirket içi kendi Docker görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e7078-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="e7078-112">Şekil 2-4 ne görüntüleri ve kayıt defterleri Docker içindeki diğer bileşenlere ilişkili gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7078-112">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="e7078-113">Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7078-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="e7078-114">**Şekil 2-4**.</span><span class="sxs-lookup"><span data-stu-id="e7078-114">**Figure 2-4**.</span></span> <span data-ttu-id="e7078-115">Sınıflandırma Docker terimleri ve kavramları</span><span class="sxs-lookup"><span data-stu-id="e7078-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="e7078-116">Kayıt defterinde görüntüleri koyma framework düzeydeki tüm bağımlılıklarını dahil olmak üzere sabit ve değişmez uygulama BITS depolamak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7078-116">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="e7078-117">Bu görüntüleri sürümlü hem de birden çok ortamlarda dağıtılan ve bu nedenle tutarlı bir dağıtım birimi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e7078-117">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="e7078-118">Özel görüntü kayıt defterleri, barındırılan şirket içi veya bulutta ne zaman önerilir:</span><span class="sxs-lookup"><span data-stu-id="e7078-118">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="e7078-119">Görüntülerinizi herkese açık şekilde nedeniyle gizliliği paylaşılması değil.</span><span class="sxs-lookup"><span data-stu-id="e7078-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="e7078-120">Görüntülerinizi seçilen dağıtım ortamınızı arasındaki en düşük ağ gecikmesini olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="e7078-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="e7078-121">Üretim ortamınıza Azure bulut ise, örneğin, büyük olasılıkla ağ gecikme süresi en az olması görüntülerinizi Azure kapsayıcı kayıt defterine depolamak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="e7078-121">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="e7078-122">Üretim ortamınıza şirket ise benzer şekilde, bir şirket içi Docker güvenilen kayıt defteri aynı yerel ağ içinde kullanılabilir olmasını istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="e7078-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e7078-123">[Önceki] (docker-terminology.md) [sonraki] (.. /NET-Core-NET-Framework-Containers/index.MD)</span><span class="sxs-lookup"><span data-stu-id="e7078-123">[Previous] (docker-terminology.md) [Next] (../net-core-net-framework-containers/index.md)</span></span>
