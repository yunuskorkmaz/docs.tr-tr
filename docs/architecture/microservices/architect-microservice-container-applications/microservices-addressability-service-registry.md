---
title: Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri
description: Mikro hizmetler mimarisinde kapsayıcı görüntü kayıtlarının rolünü anlayın.
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295882"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Mikro hizmet adreslenebilirliği ve hizmet kayıt defteri

Her microservice konumunu çözmek için kullanılan benzersiz bir ad (URL) vardır. Mikro hizmetinizin nerede çalışırsa çalıştırılsın adreslenebilir olması gerekir. Hangi bilgisayarın belirli bir microservice çalıştırdığınızı düşünmek zorunda, işler hızla kötü gidebilir. DNS'nin bir URL'yi belirli bir bilgisayara çözümlemesi gibi, mikro hizmetinizin de geçerli konumunun bulunabilmesi için benzersiz bir ada sahip olması gerekir. Mikro hizmetler, çalıştırdıkları altyapıdan bağımsız olmalarını sağlayacak adreslenebilir adlar alabilmeye ihtiyaç duyar. Bu, hizmetinizin nasıl dağıtıldığı ile nasıl keşfedildiği arasında bir etkileşim olduğu anlamına gelir, çünkü bir [hizmet kayıt defteri](https://microservices.io/patterns/service-registry.html)olması gerekir. Aynı durumda, bir bilgisayar başarısız olduğunda, kayıt defteri hizmeti nin hizmetin şu anda nerede çalıştığını gösterebilmesi gerekir.

[Hizmet kayıt defteri deseni,](https://microservices.io/patterns/service-registry.html) hizmet bulmanın önemli bir parçasıdır. Kayıt defteri, hizmet örneklerinin ağ konumlarını içeren bir veritabanıdır. Bir hizmet kayıt defterinin yüksek kullanılabilir ve güncel olması gerekir. İstemciler, hizmet kayıt defterinden elde edilen ağ konumlarını önbelleğe alabilir. Ancak, bu bilgiler sonunda güncelliğini yitiriyor ve istemciler artık hizmet örneklerini keşfedemez. Sonuç olarak, bir hizmet kayıt defteri tutarlılığı korumak için bir çoğaltma protokolü kullanan bir sunucu kümesi oluşur.

Bazı mikro hizmet dağıtım ortamlarında (kümeler olarak adlandırılır, daha sonraki bir bölümde kapsanacak), hizmet bulma yerleşiktir. Örneğin, Kubernetes (AKS) ortamına sahip bir Azure Kapsayıcı Hizmeti, hizmet örneği kaydını ve kaydını silme işlemlerini işleyebilir. Ayrıca, sunucu tarafı bulma yönlendiricisi rolünü oynayan her küme ana bilgisayarüzerinde bir proxy çalıştırAr.

## <a name="additional-resources"></a>Ek kaynaklar

- **Chris Richardson' ı. Desen: Hizmet kayıt defteri** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0' a. Hizmet Kayıt Defteri** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker' ı. Hizmet bulma** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Önceki](maintain-microservice-apis.md)
>[Sonraki](microservice-based-composite-ui-shape-layout.md)
