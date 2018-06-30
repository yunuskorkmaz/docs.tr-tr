---
title: Mikro çözümlenebilme ve hizmet kayıt defteri
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro çözümlenebilme ve hizmet kayıt defteri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ec3ccdd823e00d148bb8a97e906132f44e7fa727
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106677"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Mikro çözümlenebilme ve hizmet kayıt defteri

Her mikro hizmet konumu çözümlemek için kullanılan benzersiz bir ad (URL) sahiptir. Mikro hizmet çalıştığı her yerde adreslenebilir olması gerekir. Belirli bir mikro hizmet çalıştığı hangi bilgisayar hakkında düşünmek varsa, öğeleri hızlı bir şekilde hatalı gidebilirsiniz. DNS için belirli bir bilgisayardaki bir URL çözümleyen aynı şekilde, mikro hizmet geçerli konumuna bulunabilirlik böylece benzersiz bir ad olmalıdır. Mikro bunlar çalıştıran altyapısından bağımsız duruma adreslenebilir adları olması gerekir. Bu olması gerekir çünkü hizmetinizin nasıl dağıtıldığını ve nasıl bulunduğundan, arasındaki etkileşim olduğunu gösterir bir [hizmet kayıt defteri](https://microservices.io/patterns/service-registry.html). Bir bilgisayar başarısız olduğunda, aynı damarlı içinde kayıt defteri hizmeti hizmeti şimdi çalıştığı belirtmek kurabilmesi gerekir.

[Hizmet kayıt defteri deseni](https://microservices.io/patterns/service-registry.html) hizmet bulmayı önemli bir parçasıdır. Kayıt defteri hizmeti örnekleri ağ konumlarını içeren bir veritabanıdır. Hizmet kayıt defteri yüksek oranda kullanılabilir ve güncel olması gerekir. İstemciler hizmet kayıt defterinden alınan ağ konumlarını önbelleğe. Ancak, bu bilgileri sonunda güncel gider ve istemciler artık hizmet örnekleri bulabilir. Sonuç olarak, bir hizmet kayıt defteri tutarlılığını korumak için bir çoğaltma protokolü kullanan sunucuları kümesini oluşur.

(Bir sonraki bölümde ele alınacak kümeleri olarak adlandırılır) bazı mikro hizmet dağıtım ortamlarda, hizmet bulma yerleşiktir. Örneğin, bir Azure kapsayıcı hizmeti ortamında Kubernetes ve DC/OS Marathon ile hizmeti örneğinin kaydını işlemek ve silinmesi yapılamadı. Bunlar, ayrıca bir proxy sunucu tarafı bulma yönlendirici rol oynar her küme ana bilgisayarda çalıştırın. Hizmet kayıt defteri, Giden kutusu adlandırma hizmeti aracılığıyla da sağlayan Azure Service Fabric başka bir örnektir.

Hizmet kayıt defteri ve yardımcı olan de bu sorunu çözmek API ağ geçidi düzeni arasında belirli çakışma olduğuna dikkat edin. Örneğin, [Service Fabric Ters Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) bir API Fabrice adlandırma hizmeti üzerinde bağlı ve yardımcı olan adres çözümlemesi için iç hizmetlerin çözümlenmesi ağ geçidi uygulaması bir türde değil.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Chris Uludağ. Desen: Hizmet kayıt defteri**
    *https://microservices.io/patterns/service-registry.html*

-   **Auth0. Hizmet kayıt defteri**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **GABRIEL Schenker. Hizmet bulma**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Önceki](maintain-microservice-apis.md)
[sonraki](microservice-based-composite-ui-shape-layout.md)
