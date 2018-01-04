---
title: "Docker kapsayıcıları, görüntüler ve kayıt defterleri"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0cccead8833c63f19b359f830f555e7ff31daa1a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a>Docker kapsayıcıları, görüntüler ve kayıt defterleri

Docker kullanırken, bir uygulama veya hizmeti ve paketi ve bağımlılıklarını kapsayıcı görüntüsü oluşturun. Görüntü uygulama veya hizmet ve yapılandırma ve bağımlılıkları statik bir gösterimidir.

Uygulama veya hizmeti çalıştırmak için uygulamanın görüntü Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği. Kapsayıcılar, başlangıçta bir geliştirme ortamı veya PC sınanır.

Görüntü resimlerinin kitaplık olarak davranan bir kayıt defteri depolayın. Bir kayıt defteri üretim orchestrators dağıtırken gerekir. Docker tutar ortak kayıt defterinden [Docker hub'a](https://hub.docker.com/); diğer satıcılar görüntüleri farklı koleksiyonlar için kayıt defterleri sağlayın. Alternatif olarak, kuruluşların özel bir kayıt defteri olabilir şirket içi kendi Docker görüntüler.

Şekil 1-4 ne görüntüleri ve kayıt defterleri Docker içindeki diğer bileşenlere ilişkili gösterir. Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.

![](./media/image4.png)

Şekil 1-4: sınıflandırma Docker terimleri ve kavramları

Kayıt defterinde görüntüleri koyarak framework düzeyinde, bağımlılıklarının tümü de dahil olmak üzere sabit ve değişmez uygulama BITS depolayabilirsiniz. Ardından sürüm ve birden çok ortamlarda görüntüleri dağıtabilir ve böylece tutarlı bir dağıtım birimi sağlayın.

Özel görüntü kayıt defterleri, şirket içi barındırılan veya bulutta, aşağıdaki durumlarda önerilir:

-   Görüntülerinizi herkese açık şekilde nedeniyle gizliliği paylaşılması değil.

-   Görüntülerinizi seçilen dağıtım ortamınızı arasındaki en düşük ağ gecikmesini olmasını istiyorsunuz. Üretim ortamınıza Azure ise, örneğin, büyük olasılıkla ağ gecikme süresi en az olması görüntülerinizi Azure kapsayıcı kayıt defterine depolamak istediğiniz. Üretim ortamınıza şirket ise benzer şekilde, bir şirket içi Docker güvenilen kayıt defteri aynı yerel ağ içinde kullanılabilir olmasını istiyorsanız.

>[!div class="step-by-step"]
[Önceki] (docker-terminology.md) [sonraki] (Docker-uygulama-yaşam döngüsü/index.md)
