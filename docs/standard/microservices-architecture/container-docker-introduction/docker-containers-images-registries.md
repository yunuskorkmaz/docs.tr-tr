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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 79dccadfba066c673e8ef7ea5eaf1051a434ff3a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a>Docker kapsayıcıları, görüntüler ve kayıt defterleri

Docker kullanırken, bir geliştirici bir uygulama veya hizmet ve paketleri ve bağımlılıklarını kapsayıcı görüntüsü oluşturur. Görüntü uygulama veya hizmet ve yapılandırma ve bağımlılıkları statik bir gösterimidir.

Uygulama veya hizmeti çalıştırmak için uygulamanın görüntü Docker ana bilgisayarda çalışan bir kapsayıcı oluşturmak için örneği. Kapsayıcılar, başlangıçta bir geliştirme ortamı veya PC sınanır.

Geliştiricilerin görüntüleri görüntülerinin kitaplık olarak davranır ve üretim orchestrators dağıtırken gereken bir kayıt defteri depolamanız gerekir. Docker tutar ortak kayıt defterinden [Docker hub'a](https://hub.docker.com/); diğer satıcılar görüntüleri farklı koleksiyonlar için kayıt defterleri sağlayın. Alternatif olarak, kuruluşların özel bir kayıt defteri olabilir şirket içi kendi Docker görüntüler.

Şekil 2-4 ne görüntüleri ve kayıt defterleri Docker içindeki diğer bileşenlere ilişkili gösterir. Ayrıca birden çok kayıt defteri teklifleri satıcılardan gösterir.

![](./media/image5.PNG)

**Şekil 2-4**. Sınıflandırma Docker terimleri ve kavramları

Kayıt defterinde görüntüleri koyma framework düzeydeki tüm bağımlılıklarını dahil olmak üzere sabit ve değişmez uygulama BITS depolamak olanak sağlar. Bu görüntüleri sürümlü hem de birden çok ortamlarda dağıtılan ve bu nedenle tutarlı bir dağıtım birimi sağlayın.

Özel görüntü kayıt defterleri, barındırılan şirket içi veya bulutta ne zaman önerilir:

-   Görüntülerinizi herkese açık şekilde nedeniyle gizliliği paylaşılması değil.

-   Görüntülerinizi seçilen dağıtım ortamınızı arasındaki en düşük ağ gecikmesini olmasını istiyorsunuz. Üretim ortamınıza Azure bulut ise, örneğin, büyük olasılıkla ağ gecikme süresi en az olması görüntülerinizi Azure kapsayıcı kayıt defterine depolamak istediğiniz. Üretim ortamınıza şirket ise benzer şekilde, bir şirket içi Docker güvenilen kayıt defteri aynı yerel ağ içinde kullanılabilir olmasını istiyorsanız.

>[!div class="step-by-step"]
[Önceki] (docker-terminology.md) [sonraki] (.. /NET-Core-NET-Framework-Containers/index.MD)
