---
title: Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri
description: Mikro hizmet mimarisinde kapsayıcı görüntüsü kayıt defterlerinin rolünü anlayın.
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295882"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri

Her mikro hizmet, konumunu çözümlemek için kullanılan benzersiz bir ada (URL) sahiptir. Mikro hizmetinizin çalıştığı her yerde adreslenebilir olması gerekir. Hangi bilgisayarın belirli bir mikro hizmet çalıştırmakta olduğunu düşündüğünüzde, şeyler hızla kötü bir şekilde gidebilirler. DNS 'in belirli bir bilgisayar için bir URL 'YI çözümlediği şekilde, mikro hizmetinizin geçerli konumunun bulunabilir olması için benzersiz bir adı olması gerekir. Mikro hizmetlere, üzerinde çalıştıkları altyapıdan bağımsız olarak, adreslenebilir adlara sahip olmaları gerekir. Bu, hizmet [kayıt defteri](https://microservices.io/patterns/service-registry.html)olması gerektiğinden hizmetinizin nasıl dağıtıldığı ve nasıl keşfedildiği arasında bir etkileşim olduğunu gösterir. Aynı Vein içinde, bir bilgisayar başarısız olduğunda, kayıt defteri hizmeti hizmetin Şu anda çalıştığını belirtebilmelidir.

[Hizmet kayıt defteri stili](https://microservices.io/patterns/service-registry.html) , hizmet bulmanın önemli bir parçasıdır. Kayıt defteri, hizmet örneklerinin ağ konumlarını içeren bir veritabanıdır. Hizmet kayıt defterinin yüksek oranda kullanılabilir ve güncel olması gerekir. İstemciler, hizmet kayıt defterinden alınan ağ konumlarını önbelleğe verebilir. Bununla birlikte, bu bilgiler sonunda güncel olmayacaktır ve istemciler artık hizmet örneklerini bulamaz. Sonuç olarak, hizmet kayıt defteri tutarlılık sağlamak için çoğaltma protokolü kullanan bir sunucu kümesinden oluşur.

Bazı mikro hizmet dağıtım ortamlarında (kümeler olarak adlandırılır, sonraki bölümde ele alınacaktır), hizmet bulma yerleşik olarak bulunur. Örneğin, Kubernetes (AKS) ortamıyla bir Azure Container Service hizmet örneği kaydını işleyebilir ve kaydı iptal edebilir. Ayrıca, sunucu tarafı bulma yönlendiricisinin rolünü çalıştıran her küme konağında bir proxy çalıştırır.

## <a name="additional-resources"></a>Ek kaynaklar

- **Chris Richardson. Kalıp Hizmet kayıt defteri** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0. Hizmet kayıt defteri** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker. Hizmet bulma** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Önceki](maintain-microservice-apis.md)İleri
>[](microservice-based-composite-ui-shape-layout.md)
