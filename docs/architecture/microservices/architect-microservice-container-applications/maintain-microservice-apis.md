---
title: Mikro hizmet API’leri ve anlaşmaları oluşturma, geliştirme ve sürüm oluşturma
description: Mikrohizmet API'leri ve evrim ve sürüm dikkate alınarak sözleşmeler oluşturun, çünkü değişime ihtiyaç lar.
ms.date: 09/20/2018
ms.openlocfilehash: 1972d02d8bf7935c71bfd383707ae19ea2baded9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295459"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Mikro hizmet API’leri ve anlaşmaları oluşturma, geliştirme ve sürüm oluşturma

Microservice API, hizmet ve müşterileri arasında yapılan bir sözleşmedir. Bir mikro hizmeti ancak API sözleşmesini bozmazsanız bağımsız olarak geliştirebilirsiniz, bu nedenle sözleşme çok önemlidir. Sözleşmeyi değiştirirseniz, istemci uygulamalarınızı veya API Ağ Geçidinizi etkiler.

API tanımının yapısı, kullandığınız protokole bağlıdır. Örneğin, ileti kullanıyorsanız [(AMQP](https://www.amqp.org/)gibi), API ileti türlerinden oluşur. HTTP ve RESTful hizmetlerini kullanıyorsanız, API URL'lerden ve istek ve yanıt JSON biçimlerinden oluşur.

Ancak, ilk sözleşmeniz hakkında düşünceli olsanız bile, bir hizmet API'nin zaman içinde değişmesi gerekir. Bu durumda ve özellikle API'niz birden çok istemci uygulaması tarafından tüketilen genel bir API ise, genellikle tüm istemcileri yeni API sözleşmenize yükseltmeye zorlayamazsınız. Genellikle bir hizmet sözleşmesinin hem eski hem de yeni sürümlerinin aynı anda çalıştırılacakları şekilde bir hizmetin yeni sürümlerini artımlı olarak dağıtmanız gerekir. Bu nedenle, hizmet sürüm için bir strateji olması önemlidir.

API değişiklikleri küçük olduğunda ( örneğin, API'nize öznitelikler veya parametreler eklerseniz, eski bir API kullanan istemciler, hizmetin yeni sürümüyle geçiş yapmalı ve bunlarla çalışmalıdır. Gereken eksik öznitelikler için varsayılan değerler sağlayabilirsiniz ve istemciler herhangi bir ek yanıt özniteliklerini yok sayabilir.

Ancak, bazen bir hizmet API'sinde önemli ve uyumsuz değişiklikler yapmanız gerekir. İstemci uygulamalarını veya hizmetlerini hemen yeni sürüme yükseltmeye zorlayamayabileceğiniziçin, bir hizmetin bir süre için API'nin eski sürümlerini desteklemesi gerekir. REST gibi HTTP tabanlı bir mekanizma kullanıyorsanız, bir yaklaşım API sürüm numarasını URL'ye veya bir HTTP üstbilgisine katıştırmaktır. Ardından, aynı hizmet örneği içinde aynı anda hizmetin her iki sürümünü de uygulamak veya her biri API'nin bir sürümünü işleyen farklı örnekleri dağıtmak arasında karar verebilirsiniz. Bunun için iyi bir yaklaşım [Aracı desen](https://en.wikipedia.org/wiki/Mediator_pattern) (örneğin, [MediatR kitaplık)](https://github.com/jbogard/MediatR)bağımsız işleyicileri içine farklı uygulama sürümleri ayırmak için.

Son olarak, bir REST mimarisi kullanıyorsanız, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) hizmetlerisürüm ve evolvable API'ler izin için en iyi çözümdür.

## <a name="additional-resources"></a>Ek kaynaklar

- **Scott Hanselman' ı. ASP.NET Çekirdek RESTful Web API sürümü kolay** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **RESTful web API'yi sürümleme** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy Fielding' i. Sürüm, Hipermedya ve REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
>[Önceki](asynchronous-message-based-communication.md)
>[Sonraki](microservices-addressability-service-registry.md)
