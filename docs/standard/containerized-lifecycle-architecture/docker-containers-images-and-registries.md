---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Kayıt defterleri uygulamaları dağıtma Docker şekilde genel play önemli bir rol öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641341"
---
# <a name="docker-containers-images-and-registries"></a>Docker kapsayıcıları, görüntüleri ve kayıt defterleri

Docker'ı kullanarak bir uygulama veya hizmeti ve paketi ve bağımlılıkları bir kapsayıcı görüntüsü oluşturduğunuzda. Görüntü uygulamayı veya hizmeti ve kendi yapılandırma ve bağımlılıklarla statik bir gösterimidir.

Uygulamanızı veya hizmetinizi çalıştırmak için uygulamanın resmi Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği oluşturulur. Kapsayıcı başlangıçta bir geliştirme ortamı veya bilgisayar test edilmez.

Görüntü kitaplığı davranan bir kayıt defteri, görüntüleri depolayın. Bir kayıt defteri için üretim düzenleyicileri dağıtırken gerekir. Genel bir kayıt defterinden docker tutar [Docker Hub](https://hub.docker.com/); diğer satıcıları görüntüleri dahil olmak üzere, farklı koleksiyonlar için kayıt defterleri sağlayan [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternatif olarak, kuruluşlar, özel bir kayıt defteri sahip olabilir, kendi Docker görüntüleri için şirket içi.

Şekil 1-4 nasıl görüntüler ve Docker kayıt defterleri için diğer bileşenleri ilişkilendirilmesi gösterir. Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.

![Docker temel taksonomisinde: Kayıt defteri, görüntüleri depolanan ve hizmeti veya web uygulaması çalıştırmak için kapsayıcılar oluşturmak için çekilmesi kullanılabilir olduğu gibi bir bookshelf olduğu. Özel Docker kayıt defterleri şirket içi vardır ve herkese açık bulut. Docker hub'ı genel bir kayıt defteri Docker ile Docker Trusted Registry kurumsal sınıf çözüm, Azure, Azure Container Registry sunar saklanır. Kapsayıcı kayıt defterleri AWS, Google ve diğerleri de var.](./media/image4.png)

**Şekil 1-4**. Docker terimleri ve kavramları'nin Taksonomisi

Kayıt defterindeki görüntüleri koyarak çerçevesi düzeyinde, bağımlılıklarının tümü de dahil olmak üzere, statik ve sabit uygulama BITS depolayabilirsiniz. Ardından sürüm ve birden çok ortama görüntülerde dağıtabilir ve bu nedenle, tutarlı dağıtım birimi sağlayın.

Özel görüntü kayıt defterleri, barındırılan şirket içinde veya bulutta, ne zaman önerilir:

- Nedeniyle gizlilik görüntülerinizin herkese açık şekilde paylaşılmamalı.

- Görüntüleri ve seçilen dağıtım ortamınız arasında düşük ağ gecikme süresine sahiptir istiyorsunuz. Üretim ortamınızı Azure ise, örneğin, büyük olasılıkla görüntülerinizi depolamak istediğiniz [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) ağ gecikme süresi çok az olmasını sağlayın. Üretim ortamınıza şirket içinde ise benzer şekilde, bu, bir şirket içi Docker Trusted Registry aynı yerel ağda kullanılabilir olmasını isteyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](docker-terminology.md)
>[İleri](road-to-modern-applications-based-on-containers.md)
