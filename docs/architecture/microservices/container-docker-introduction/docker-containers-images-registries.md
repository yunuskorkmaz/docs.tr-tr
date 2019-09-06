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
# <a name="docker-containers-images-and-registries"></a>Docker kapsayıcıları, görüntüleri ve kayıt defterleri

Bir geliştirici, Docker kullanırken bir uygulama veya hizmet oluşturur ve onun bağımlılıklarını ve onun bağımlılıklarını bir kapsayıcı görüntüsüne paketler. Görüntü, uygulamanın veya hizmetin statik bir gösterimidir ve yapılandırma ve bağımlılıkları.

Uygulamayı veya hizmeti çalıştırmak için, uygulamanın görüntüsü, Docker konağında çalışacak bir kapsayıcı oluşturmak için oluşturulur. Kapsayıcılar başlangıçta bir geliştirme ortamında veya bılgısayarda test edilir.

Geliştiriciler görüntüleri bir kayıt defteri halinde depolamalıdır ve bu, görüntü kitaplığı gibi davranır ve üretim düzenleyicilerine dağıtıldığında gereklidir. Docker, [Docker Hub](https://hub.docker.com/)aracılığıyla ortak bir kayıt defteri sağlar; diğer satıcılar, [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)dahil olmak üzere farklı görüntü koleksiyonlarına yönelik kayıt defterleri sağlar. Alternatif olarak, kuruluşlar kendi Docker görüntüleri için şirket içinde özel bir kayıt defterine sahip olabilir.

Şekil 2-4, Docker 'daki görüntülerin ve kayıt defterlerinin diğer bileşenlerle nasıl ilişkisi olduğunu gösterir. Ayrıca, satıcıların birden çok kayıt defteri teklifini gösterir.

![Docker 'da temel taksonomi: Kayıt defteri, görüntülerin depolandığı ve hizmetleri ya da Web Apps 'i çalıştırmak üzere kapsayıcılar oluşturmak için çekilmek üzere kullanılabilecek bir Bookshelf gibidir. Şirket içinde ve genel bulutta özel Docker kayıt defterleri vardır. Docker Hub, Docker tarafından korunan ortak bir kayıt defteridir. Docker güvenilen kayıt defteri kurumsal düzeyde bir çözümde, Azure Azure Container Registry sunar. AWS, Google ve diğer kullanıcıların kapsayıcı kayıt defterleri de vardır.](./media/image5.PNG)

**Şekil 2-4**. Docker hüküm ve kavramlarının sınıflandırması

Görüntüleri bir kayıt defterine koymak, tüm bağımlılıkları dahil olmak üzere statik ve değişmez uygulama bitlerini bir çerçeve düzeyinde depolamanıza olanak sağlar. Bu görüntüler daha sonra birden fazla ortamda sürümlenebilir ve dağıtılabilir ve bu nedenle tutarlı bir dağıtım birimi sağlar.

Şirket içinde veya bulutta barındırılan özel görüntü kayıt defterleri şu durumlarda önerilir:

- Gizli olmaması nedeniyle görüntülerinizin genel olarak paylaşılmaması gerekir.

- Resimleriniz ve seçtiğiniz dağıtım ortamınız arasında en düşük ağ gecikme süresine sahip olmak istiyorsunuz. Örneğin, üretim ortamınız Azure bulutunuz ise, büyük ihtimalle, ağ gecikmesi en düşük olacak şekilde [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) görüntülerini depolamak isteyebilirsiniz. Benzer bir şekilde, üretim ortamınız şirket içindeyse, aynı yerel ağ içinde şirket içi bir Docker güvenilir kayıt defteri kullanılabilir olmasını isteyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](docker-terminology.md)İleri
>[](../net-core-net-framework-containers/index.md)
