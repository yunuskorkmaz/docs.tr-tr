---
title: Docker kapsayıcıları, görüntüler ve kayıt defterleri
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: ff5a1f3e4b09ac9f7ea600d3f127523b96fcce55
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106369"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="87c82-103">Docker kapsayıcıları, görüntüler ve kayıt defterleri</span><span class="sxs-lookup"><span data-stu-id="87c82-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="87c82-104">Docker kullanırken, bir uygulama veya hizmeti ve paketi ve bağımlılıklarını kapsayıcı görüntüsü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87c82-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="87c82-105">Görüntü uygulama veya hizmet ve yapılandırma ve bağımlılıkları statik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="87c82-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="87c82-106">Uygulama veya hizmeti çalıştırmak için uygulamanın görüntü Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği.</span><span class="sxs-lookup"><span data-stu-id="87c82-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="87c82-107">Kapsayıcılar, başlangıçta bir geliştirme ortamı veya PC sınanır.</span><span class="sxs-lookup"><span data-stu-id="87c82-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="87c82-108">Görüntü resimlerinin kitaplık olarak davranan bir kayıt defteri depolayın.</span><span class="sxs-lookup"><span data-stu-id="87c82-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="87c82-109">Bir kayıt defteri üretim orchestrators dağıtırken gerekir.</span><span class="sxs-lookup"><span data-stu-id="87c82-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="87c82-110">Docker tutar ortak kayıt defterinden [Docker hub'a](https://hub.docker.com/); diğer satıcılar görüntüleri farklı koleksiyonlar için kayıt defterleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="87c82-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="87c82-111">Alternatif olarak, kuruluşların özel bir kayıt defteri olabilir şirket içi kendi Docker görüntüler.</span><span class="sxs-lookup"><span data-stu-id="87c82-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="87c82-112">Şekil 1-4 ne görüntüleri ve kayıt defterleri Docker içindeki diğer bileşenlere ilişkili gösterir.</span><span class="sxs-lookup"><span data-stu-id="87c82-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="87c82-113">Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.</span><span class="sxs-lookup"><span data-stu-id="87c82-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="87c82-114">Şekil 1-4: sınıflandırma Docker terimleri ve kavramları</span><span class="sxs-lookup"><span data-stu-id="87c82-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="87c82-115">Kayıt defterinde görüntüleri koyarak framework düzeyinde, bağımlılıklarının tümü de dahil olmak üzere sabit ve değişmez uygulama BITS depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87c82-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="87c82-116">Ardından sürüm ve birden çok ortamlarda görüntüleri dağıtabilir ve böylece tutarlı bir dağıtım birimi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="87c82-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="87c82-117">Özel görüntü kayıt defterleri, şirket içi barındırılan veya bulutta, aşağıdaki durumlarda önerilir:</span><span class="sxs-lookup"><span data-stu-id="87c82-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="87c82-118">Görüntülerinizi herkese açık şekilde nedeniyle gizliliği paylaşılması değil.</span><span class="sxs-lookup"><span data-stu-id="87c82-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="87c82-119">Görüntülerinizi seçilen dağıtım ortamınızı arasındaki en düşük ağ gecikmesini olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="87c82-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="87c82-120">Üretim ortamınıza Azure ise, örneğin, büyük olasılıkla ağ gecikme süresi en az olması görüntülerinizi Azure kapsayıcı kayıt defterine depolamak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="87c82-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="87c82-121">Üretim ortamınıza şirket ise benzer şekilde, bir şirket içi Docker güvenilen kayıt defteri aynı yerel ağ içinde kullanılabilir olmasını istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="87c82-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="87c82-122">[Önceki](docker-terminology.md)
[sonraki](Docker-application-lifecycle/index.md)</span><span class="sxs-lookup"><span data-stu-id="87c82-122">[Previous](docker-terminology.md)
[Next](Docker-application-lifecycle/index.md)</span></span>
