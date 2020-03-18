---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Kayıtların uygulamaları dağıtma da Docker şekilde genel olarak oynadığı temel rolü öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: bfef21cab7be89abaf33b89366d7cff2115a7cc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72770924"
---
# <a name="docker-containers-images-and-registries"></a>Docker kapsayıcıları, görüntüleri ve kayıt defterleri

Docker kullanırken, bir uygulama veya hizmet oluşturur ve onu ve bağımlılıklarını bir kapsayıcı görüntüsüne paketlersiniz. Görüntü, uygulama nın veya hizmetin ve onun yapılandırmasının ve bağımlılıklarının statik bir temsilidir.

Uygulamayı veya hizmeti çalıştırmak için, uygulamanın görüntüsü Docker ana bilgisayarda çalışacak bir kapsayıcı oluşturmak için anında oluşturulur. Kapsayıcılar başlangıçta bir geliştirme ortamında veya bilgisayarda test edilir.

Görüntüleri, resimlerin kitaplığı gibi davranan bir kayıt defterinde depolarsınız. Prodüksiyon orkestratörlerine dağıtılırken bir kayıt defterine ihtiyacınız vardır. Docker, [Docker Hub](https://hub.docker.com/)üzerinden genel kayıt defteri tutar; diğer satıcılar, [Azure Kapsayıcı Kayıt Defteri](https://azure.microsoft.com/services/container-registry/)de dahil olmak üzere farklı resim koleksiyonları için kayıt defterleri sağlar. Alternatif olarak, işletmelerin kendi Docker görüntüleri için şirket içinde özel bir kayıt olabilir.

Şekil 1-4, Docker'daki görüntülerin ve kayıt defterlerinin diğer bileşenlerle nasıl ilişkili olduğunu gösterir. Ayrıca satıcılardan gelen birden çok kayıt defteri sunularını da gösterir.

![Docker'daki temel taksonomigösteren bir diyagram.](./media/docker-containers-images-and-registries/taxonomy-docker-terms-concepts.png)

**Şekil 1-4**. Docker terim ve kavramlarının taksonomisi

Kayıt defteri, görüntülerin depolandığı ve hizmetleri veya web uygulamalarını çalıştırmak için kapsayıcılar oluşturmak için çekilebildiği bir kitaplık gibidir. Şirket içinde ve genel bulutta özel Docker kayıtları vardır. Docker Hub, Docker Trusted Registry boyunca kurumsal sınıf bir çözüm olan Docker Tarafından tutulan bir genel kayıt defteridir, Azure Azure Konteyner Kayıt Defteri'ni sunar. AWS, Google ve diğerleri de konteyner kayıtları var.

Görüntüleri bir kayıt defterine koyarak, tüm bağımlılıkları da dahil olmak üzere statik ve değişmez uygulama bitlerini çerçeve düzeyinde depolayabilirsiniz. Daha sonra görüntüleri birden çok ortamda sürümleyebilir ve dağıtabilir ve böylece tutarlı bir dağıtım birimi sağlayabilirsiniz.

Şirket içinde veya bulutta barındırılan özel görüntü kayıtları aşağıdaki durumlarda önerilir:

- Resimleriniz gizlilik nedeniyle herkese açık olarak paylaşılmamalıdır.

- Resimleriniz ile seçtiğiniz dağıtım ortamı arasında minimum ağ gecikmesi olmasını istiyorsunuz. Örneğin, üretim ortamınız Azure ise, ağ gecikmesi en az olacak şekilde resimlerinizi [Azure Kapsayıcı Kayıt Defteri'nde](https://azure.microsoft.com/services/container-registry/) depolamak isteyebilirsiniz. Benzer bir şekilde, üretim ortamınız şirket içindeyse, aynı yerel ağ içinde şirket içi Docker Trusted Registry'ye sahip olmak isteyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](docker-terminology.md)
>[Sonraki](road-to-modern-applications-based-on-containers.md)
