---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: af235280c985d20f9e6a2ee6096edbe6c3aad63a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53142755"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="5e681-103">Docker kapsayıcıları, görüntüleri ve kayıt defterleri</span><span class="sxs-lookup"><span data-stu-id="5e681-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="5e681-104">Docker'ı kullanarak bir uygulama veya hizmeti ve paketi ve bağımlılıkları bir kapsayıcı görüntüsü oluşturduğunuzda.</span><span class="sxs-lookup"><span data-stu-id="5e681-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="5e681-105">Görüntü uygulamayı veya hizmeti ve kendi yapılandırma ve bağımlılıklarla statik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="5e681-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="5e681-106">Uygulamanızı veya hizmetinizi çalıştırmak için uygulamanın resmi Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5e681-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="5e681-107">Kapsayıcı başlangıçta bir geliştirme ortamı veya bilgisayar test edilmez.</span><span class="sxs-lookup"><span data-stu-id="5e681-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="5e681-108">Görüntü kitaplığı hareket eden bir kayıt defteri, görüntüleri depolayın.</span><span class="sxs-lookup"><span data-stu-id="5e681-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="5e681-109">Bir kayıt defteri için üretim düzenleyicileri dağıtırken gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e681-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="5e681-110">Genel bir kayıt defterinden docker tutar [Docker Hub](https://hub.docker.com/); diğer satıcıları görüntüleri farklı koleksiyonlar için kayıt defterleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5e681-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="5e681-111">Alternatif olarak, kuruluşlar, özel bir kayıt defteri sahip olabilir, kendi Docker görüntüleri için şirket içi.</span><span class="sxs-lookup"><span data-stu-id="5e681-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="5e681-112">Şekil 1-4 nasıl görüntüler ve Docker kayıt defterleri için diğer bileşenleri ilişkilendirilmesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e681-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="5e681-113">Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e681-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="5e681-114">Şekil 1-4: Docker terimleri ve kavramları'nin Taksonomisi</span><span class="sxs-lookup"><span data-stu-id="5e681-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="5e681-115">Kayıt defterindeki görüntüleri koyarak çerçevesi düzeyinde, bağımlılıklarının tümü de dahil olmak üzere, statik ve sabit uygulama BITS depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e681-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="5e681-116">Ardından sürüm ve birden çok ortama görüntülerde dağıtabilir ve bu nedenle, tutarlı dağıtım birimi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5e681-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="5e681-117">Özel görüntü kayıt defterleri, şirket içinde barındırılan veya bulutta, aşağıdaki durumlarda önerilir:</span><span class="sxs-lookup"><span data-stu-id="5e681-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="5e681-118">Nedeniyle gizlilik görüntülerinizin herkese açık şekilde paylaşılmamalı.</span><span class="sxs-lookup"><span data-stu-id="5e681-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="5e681-119">Görüntüleri ve seçilen dağıtım ortamınız arasında düşük ağ gecikme süresine sahiptir istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="5e681-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="5e681-120">Üretim ortamınızı Azure ise, örneğin, büyük olasılıkla ağ gecikme süresi çok az olması görüntülerinizi Azure Container Registry'de depolamak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="5e681-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="5e681-121">Üretim ortamınıza şirket içinde ise benzer şekilde, bu, bir şirket içi Docker Trusted Registry aynı yerel ağda kullanılabilir olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e681-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5e681-122">[Önceki](docker-terminology.md)
>[İleri](Docker-application-lifecycle/index.md)</span><span class="sxs-lookup"><span data-stu-id="5e681-122">[Previous](docker-terminology.md)
[Next](Docker-application-lifecycle/index.md)</span></span>