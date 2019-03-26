---
title: Oluşturma, geliştirme ve sürüm oluşturma mikro hizmet API'leri ve anlaşmaları
description: Mikro hizmet API'leri oluşturmak ve gereksinimleriniz değiştiğinde uygun evrimi ve sürüm çünkü dikkate sözleşme.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 6580418ea04d64650cefe2f4c91f03e3f40a058f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466055"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Oluşturma, geliştirme ve sürüm oluşturma mikro hizmet API'leri ve anlaşmaları

Mikro hizmet API, hizmet ve istemcileri arasında bir sözleşmedir. Bir mikro hizmet bağımsız olarak yalnızca çok önemli sözleşme, bu yüzden API sözleşmesinin bölmediğinizden varsa gelişmek mümkün olacaktır. Sözleşme değiştirirseniz, istemci uygulamalarınız veya API ağ geçidinizin etkiler.

API tanımı doğasını hangi protokolünü kullandığınız bağlıdır. Örneğin, Mesajlaşma kullanıyorsanız (gibi [AMQP](https://www.amqp.org/)), ileti türlerini API oluşur. HTTP ve RESTful hizmetlerini kullanıyorsanız, API URL ve istek ve yanıt JSON biçimleri oluşur.

Ancak, ilk sözleşmeniz hakkında özenli olsa bile, bir hizmeti API zamanla değiştirmeniz gerekir. Bu durumda — ve özellikle API'NİZİN birden çok istemci uygulamalar tarafından kullanılan ortak bir API olduğunda — genellikle tüm istemcilerin yeni API sözleşmesine yükseltme tutamaz. Genellikle yeni bir hizmet sözleşmesini eski ve yeni sürümleri aynı anda çalışan bir şekilde bir hizmet sürümlerini artımlı olarak dağıtmanız gerekebilir. Bu nedenle, hizmet sürümü oluşturma için bir stratejiniz olması önemlidir.

API değişiklikleri API'nize öznitelikleri veya parametreleri eklerseniz gibi küçük olduğunda, daha eski bir API kullanan istemciler geçin ve hizmetin yeni sürümle çalışır. Gerekli olan eksik öznitelikler için varsayılan değerler sağlamak mümkün olabilir ve istemcilerin herhangi bir ek yanıt özniteliği yok saymak mümkün olabilir.

Ancak, bazen büyük ve uyumsuz değişiklik, bir hizmeti API'sine gerekir. İstemci uygulamaları veya hizmetleri hemen yeni sürüme yükseltmek için zorlamak mümkün olmayabilir çünkü bir hizmeti API eski sürümleri için belirli bir süre desteklemesi gerekir. Bir HTTP tabanlı mekanizması gibi REST kullanıyorsanız, bir URL veya bir HTTP üst bilgisi API sürüm numarasını ekleyin yaklaşımdır. Sonra iki sürümü de aynı hizmet örneği hizmetinde aynı anda uygulama veya her bir API sürümünü işlemek farklı örnekleri dağıtma arasında karar verebilirsiniz. Bunun iyi bir yaklaşımdır [Dünyası deseni](https://en.wikipedia.org/wiki/Mediator_pattern) (örneğin, [MediatR Kitaplığı](https://github.com/jbogard/MediatR)) farklı sürümler bağımsız işleyicileri ayırmak için.

Son olarak, bir REST mimarisi kullanıyorsanız [gösterimde](https://www.infoq.com/articles/mark-baker-hypermedia) hizmetlerinizi ve evolvable API'leri sağlayan sürüm oluşturma için en iyi bir çözümdür.

## <a name="additional-resources"></a>Ek kaynaklar

- **Scott Hanselman. ASP.NET Core RESTful Web API'si sürümü oluşturma artık daha kolay** \
  [https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

- **RESTful web API'si sürümü oluşturma** \
  [https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

- **Roy Fielding. Sürüm oluşturma, iletilir ve REST** \
  [https://www.infoq.com/articles/roy-fielding-on-versioning](https://www.infoq.com/articles/roy-fielding-on-versioning)

>[!div class="step-by-step"]
>[Önceki](asynchronous-message-based-communication.md)
>[İleri](microservices-addressability-service-registry.md)