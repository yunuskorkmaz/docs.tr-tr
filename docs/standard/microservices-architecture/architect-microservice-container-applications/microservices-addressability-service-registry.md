---
title: Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri
description: Mikro hizmet mimarisi kapsayıcı görüntüsünü kayıt defterleri rolünü anlayın.
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690467"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri

Her mikro hizmet konumu çözümlemek için kullanılan benzersiz bir adı (URL) vardır. Kendi mikro hizmet, çalıştığı her yerde adreslenebilir olması gerekiyor. Belirli bir mikro hizmet çalıştığı hangi bilgisayar hakkında düşünmek varsa, öğeleri hızlı bir şekilde hatalı gidebilirsiniz. DNS, belirli bir bilgisayar için bir URL çözümleyen aynı şekilde, mikro hizmet geçerli konumuna bulunabilir olmasını sağlama benzersiz bir ad olmalıdır. Mikro hizmetler, çalıştırdığınız bilgisayarda altyapısından bağımsız hale adreslenebilir adları olması gerekir. Bu olması gerekir çünkü hizmetinizin nasıl dağıtıldığını ve nasıl bulunduğunda, arasında etkileşim olduğunu gelir bir [hizmet kayıt defteri](https://microservices.io/patterns/service-registry.html). Bir bilgisayar başarısız olduğunda, aynı damarlı kayıt defteri hizmeti hizmet artık çalıştığı belirtmek mümkün olması gerekir.

[Hizmet kayıt defteri düzeni](https://microservices.io/patterns/service-registry.html) hizmet bulma işleminin önemli bir parçasıdır. Kayıt defteri hizmeti örnekleri ağ konumlarını içeren bir veritabanıdır. Bir hizmet kayıt defteri yüksek oranda kullanılabilir ve güncel olması gerekir. İstemcileri, hizmet kayıt defterinden alınan ağ konumlarını önbelleğe alınamadı. Ancak, bu bilgileri sonunda güncel gider ve istemciler artık hizmet örnekleri bulabilir. Sonuç olarak, bir hizmet kayıt defteri tutarlılık sağlamak için bir çoğaltma protokolünü kullanan sunucularının bir kümesini içerir.

(Bir sonraki bölümde ele alınacak kümeleri denir) bazı mikro hizmet dağıtım ortamlarında, hizmet bulma yerleşik olarak sunulmaktadır. Örneğin, bir Azure Container Service (AKS) Kubernetes ortamı ile hizmeti örneğinin kaydını işlemek ve kayıt kaldırma. Ayrıca bir proxy sunucu tarafı bulma yönlendirici rol oynar her küme ana bilgisayarında çalıştırır.

## <a name="additional-resources"></a>Ek kaynaklar

- **Chris Richardson. Desen: Hizmet kayıt defteri** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0. Hizmet kayıt defteri** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker. Hizmet bulma** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Önceki](maintain-microservice-apis.md)
>[İleri](microservice-based-composite-ui-shape-layout.md)
