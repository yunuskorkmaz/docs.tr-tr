---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker kapsayıcıları, görüntüleri ve kayıt defterleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: f10d7d03bbf88ed8f7a89a5d3919a39b3c124ae0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130240"
---
# <a name="docker-containers-images-and-registries"></a>Docker kapsayıcıları, görüntüleri ve kayıt defterleri

Docker'ı kullanarak, bir geliştirici bir uygulama veya hizmet ve paketleri ve bağımlılıklarını kapsayıcı görüntüsüne oluşturur. Görüntü uygulamayı veya hizmeti ve kendi yapılandırma ve bağımlılıklarla statik bir gösterimidir.

Uygulamanızı veya hizmetinizi çalıştırmak için uygulamanın resmi Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği oluşturulur. Kapsayıcı başlangıçta bir geliştirme ortamı veya bilgisayar test edilmez.

Geliştiriciler, bir görüntü kitaplığı olarak davranır ve üretim düzenleyiciler için dağıtırken gereken bir kayıt defteri görüntüleri depolamanız gerekir. Genel bir kayıt defterinden docker tutar [Docker Hub](https://hub.docker.com/); diğer satıcıları görüntüleri dahil olmak üzere, farklı koleksiyonlar için kayıt defterleri sağlayan [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternatif olarak, kuruluşlar, özel bir kayıt defteri sahip olabilir, kendi Docker görüntüleri için şirket içi.

Şekil 2-4 nasıl görüntüler ve Docker kayıt defterleri için diğer bileşenleri ilişkilendirilmesi gösterir. Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.

![Docker temel taksonomisinde: Kayıt defteri, görüntüleri depolanan ve hizmeti veya web uygulaması çalıştırmak için kapsayıcılar oluşturmak için çekilmesi kullanılabilir olduğu gibi bir bookshelf olduğu. Özel Docker kayıt defterleri şirket içi vardır ve herkese açık bulut. Docker hub'ı genel bir kayıt defteri Docker ile Docker Trusted Registry kurumsal sınıf çözüm, Azure, Azure Container Registry sunar saklanır. Kapsayıcı kayıt defterleri AWS, Google ve diğerleri de var.](./media/image5.PNG)

**Şekil 2-4**. Docker terimleri ve kavramları'nin Taksonomisi

Kayıt defterindeki görüntüleri yerleştirme çerçevesi düzeyinde, tüm bağımlılıklar dahil olmak üzere, statik ve sabit uygulama BITS depolamanıza olanak tanıyan. Bu görüntüleri, ardından oluşturulan ve dağıtılan birden çok ortamda ve bu nedenle, tutarlı dağıtım birimi sağlayın.

Özel görüntü kayıt defterleri, barındırılan şirket içinde veya bulutta, ne zaman önerilir:

-   Nedeniyle gizlilik görüntülerinizin herkese açık şekilde paylaşılmamalı.

-   Görüntüleri ve seçilen dağıtım ortamınız arasında düşük ağ gecikme süresine sahiptir istiyorsunuz. Üretim ortamınızı Azure bulut ise, örneğin, büyük olasılıkla görüntülerinizi depolamak istediğiniz [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) ağ gecikme süresi çok az olması. Üretim ortamınıza şirket içinde ise benzer şekilde, bu, bir şirket içi Docker Trusted Registry aynı yerel ağda kullanılabilir olmasını isteyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](docker-terminology.md)
>[İleri](../net-core-net-framework-containers/index.md)