---
title: Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ec0617c5a5c1861f3596e12f3d7a7017a448239e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865573"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri

Her mikro hizmet konumu çözümlemek için kullanılan benzersiz bir adı (URL) vardır. Kendi mikro hizmet, çalıştığı her yerde adreslenebilir olması gerekiyor. Belirli bir mikro hizmet çalıştığı hangi bilgisayar hakkında düşünmek varsa, öğeleri hızlı bir şekilde hatalı gidebilirsiniz. DNS, belirli bir bilgisayar için bir URL çözümleyen aynı şekilde, mikro hizmet geçerli konumuna bulunabilir olmasını sağlama benzersiz bir ad olmalıdır. Mikro hizmetler, çalıştırıldıkları altyapının bağımsız hale adreslenebilir adları olması gerekir. Bu olması gerekir çünkü hizmetinizin nasıl dağıtıldığını ve nasıl bulunduğunda, arasında etkileşim olduğunu gelir bir [hizmet kayıt defteri](https://microservices.io/patterns/service-registry.html). Bir bilgisayar başarısız olduğunda, aynı damarlı kayıt defteri hizmeti hizmet artık çalıştığı belirtmek mümkün olması gerekir.

[Hizmet kayıt defteri düzeni](https://microservices.io/patterns/service-registry.html) hizmet bulma işleminin önemli bir parçasıdır. Kayıt defteri hizmeti örnekleri ağ konumlarını içeren bir veritabanıdır. Bir hizmet kayıt defteri yüksek oranda kullanılabilir ve güncel olması gerekir. İstemcileri, hizmet kayıt defterinden alınan ağ konumlarını önbelleğe alınamadı. Ancak, bu bilgileri sonunda güncel gider ve istemciler artık hizmet örnekleri bulabilir. Sonuç olarak, bir hizmet kayıt defteri tutarlılık sağlamak için bir çoğaltma protokolünü kullanan sunucularının bir kümesini içerir.

(Bir sonraki bölümde ele alınacak kümeleri denir) bazı mikro hizmet dağıtım ortamlarında, hizmet bulma yerleşik olarak sunulmaktadır. Örneğin, bir Azure Container Service ortamında, Kubernetes Marathon ile DC/OS hizmeti örneğinin kaydını işlemek ve kayıt kaldırma. Bunlar ayrıca bir proxy sunucu tarafı bulma yönlendirici rol oynar her küme ana bilgisayarda çalıştırın. Ayrıca, kullanıma hazır adlandırma hizmeti aracılığıyla bir hizmet kayıt defteri sağlayan Azure Service Fabric, başka bir örnektir.

Hizmet kayıt defteri ve yardımcı olan de bu sorunu çözmek API ağ geçidi düzeni arasında belirli çakışma olduğuna dikkat edin. Örneğin, [Service Fabric Reverse Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) API yardımcı olan adres çözümlemesi için dahili Hizmet çözmek ve Service Fabric adlandırma ağ geçidi üzerinde temel ağ geçidi uygulaması türüdür.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Chris Uludağ. Desen: Hizmet kayıt defteri**
    *https://microservices.io/patterns/service-registry.html*

-   **Auth0. Hizmet kayıt defteri**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabriel Schenker. Hizmet bulma**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Önceki](maintain-microservice-apis.md)
[İleri](microservice-based-composite-ui-shape-layout.md)
