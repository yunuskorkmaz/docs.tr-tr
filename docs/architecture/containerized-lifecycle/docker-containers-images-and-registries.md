---
title: Docker kapsayıcıları, görüntüleri ve kayıt defterleri
description: Kayıt defterlerinin, uygulamaları dağıtmanın Docker yolunda genel olarak oynamakta olduğu anahtar rolü öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295660"
---
# <a name="docker-containers-images-and-registries"></a>Docker kapsayıcıları, görüntüleri ve kayıt defterleri

Docker kullanırken bir uygulama veya hizmet oluşturur ve onun bağımlılıklarını bir kapsayıcı görüntüsüne paketleyebilir. Görüntü, uygulamanın veya hizmetin statik bir gösterimidir ve yapılandırma ve bağımlılıkları.

Uygulamayı veya hizmeti çalıştırmak için, uygulamanın görüntüsü, Docker konağında çalışacak bir kapsayıcı oluşturmak için oluşturulur. Kapsayıcılar başlangıçta bir geliştirme ortamında veya bılgısayarda test edilir.

Görüntüleri bir görüntü kitaplığı gibi davranan bir kayıt defterine depoladığınızda. Üretim düzenleyicilerine dağıtım yaparken bir kayıt defteri gerekir. Docker, [Docker Hub](https://hub.docker.com/)aracılığıyla ortak bir kayıt defteri sağlar; diğer satıcılar, [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)dahil olmak üzere farklı görüntü koleksiyonlarına yönelik kayıt defterleri sağlar. Alternatif olarak, kuruluşlar kendi Docker görüntüleri için şirket içinde özel bir kayıt defterine sahip olabilir.

Şekil 1-4, Docker 'daki görüntülerin ve kayıt defterlerinin diğer bileşenlerle nasıl ilişkisi olduğunu gösterir. Ayrıca, satıcıların birden çok kayıt defteri teklifini gösterir.

![Docker 'da temel taksonomi: Kayıt defteri, görüntülerin depolandığı ve hizmetleri ya da Web Apps 'i çalıştırmak üzere kapsayıcılar oluşturmak için çekilmek üzere kullanılabilecek bir Bookshelf gibidir. Şirket içinde ve genel bulutta özel Docker kayıt defterleri vardır. Docker Hub, Docker tarafından korunan ortak bir kayıt defteridir. Docker güvenilen kayıt defteri kurumsal düzeyde bir çözümde, Azure Azure Container Registry sunar. AWS, Google ve diğer kullanıcıların kapsayıcı kayıt defterleri de vardır.](./media/image4.png)

**Şekil 1-4**. Docker hüküm ve kavramlarının sınıflandırması

Görüntüleri bir kayıt defterine yerleştirerek, tüm bağımlılıkları dahil olmak üzere statik ve değişmez uygulama bitlerini bir çerçeve düzeyinde saklayabilirsiniz. Daha sonra görüntüleri birden çok ortamda dağıtıp dağıtabilir ve böylece tutarlı bir dağıtım birimi sağlayabilirsiniz.

Şirket içinde veya bulutta barındırılan özel görüntü kayıt defterleri şu durumlarda önerilir:

- Gizli olmaması nedeniyle görüntülerinizin genel olarak paylaşılmaması gerekir.

- Resimleriniz ve seçtiğiniz dağıtım ortamınız arasında en düşük ağ gecikme süresine sahip olmak istiyorsunuz. Örneğin, üretim ortamınız Azure ise, büyük olasılıkla, ağ gecikmesi en düşük olması için görüntülerinizi [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) saklamak isteyeceksiniz. Benzer bir şekilde, üretim ortamınız şirket içindeyse, aynı yerel ağ içinde şirket içi bir Docker güvenilir kayıt defteri kullanılabilir olmasını isteyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](docker-terminology.md)İleri
>[](road-to-modern-applications-based-on-containers.md)
