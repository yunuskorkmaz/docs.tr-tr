---
title: Mikro hizmet API’leri ve anlaşmaları oluşturma, geliştirme ve sürüm oluşturma
description: Gereksinimler değiştikçe, gelişleri ve sürüm oluşturmayı ele alarak mikro hizmet API 'Leri ve sözleşmeleri oluşturun.
ms.date: 09/20/2018
ms.openlocfilehash: 9164bfd12df18a88ac187c8962f0afc80b702881
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557678"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Mikro hizmet API’leri ve anlaşmaları oluşturma, geliştirme ve sürüm oluşturma

Mikro hizmet API 'SI, hizmet ve istemcileri arasında bir anlaşmada bulunur. Bir mikro hizmeti yalnızca API sözleşmesini bozmadıysanız bağımsız olarak geliştirebilirsiniz, bu da sözleşmenin bu kadar önemli olduğu anlamına gelir. Sözleşmeyi değiştirirseniz, istemci uygulamalarınızı veya API ağ geçidinizi etkileyecektir.

API tanımının doğası, kullanmakta olduğunuz protokole bağlıdır. Örneğin, mesajlaşma kullanıyorsanız ( [AMQP](http://www.amqp.org/)gibi), API ileti türlerinden oluşur. HTTP ve yeniden deneme Hizmetleri kullanıyorsanız, API, URL 'Lerden ve istek ve yanıt JSON biçimlerinden oluşur.

Ancak, ilk sözleşmeniz hakkında düşünceli olsanız bile, bir hizmet API 'sinin zaman içinde değişiklik yapması gerekir. Bu gerçekleştiğinde — ve API 'niz birden çok istemci uygulaması tarafından tüketilen ortak bir API ise, genellikle tüm istemcilerin yeni API sözleşmenizi yükseltmesine izin verilmez. Genellikle bir hizmetin yeni sürümlerini, bir hizmet sözleşmesinin hem eski hem de yeni sürümlerinin aynı anda çalıştığı bir şekilde artımlı olarak dağıtmanız gerekir. Bu nedenle, hizmet sürümü oluşturma stratejiniz için bir strateji olması önemlidir.

API değişiklikleri küçük olduğunda, API 'nize öznitelikler veya parametreler eklerseniz, daha eski bir API kullanan istemciler hizmetin yeni sürümü ile anahtar ve çalışır olmalıdır. Gerekli olan eksik özniteliklerin varsayılan değerlerini sağlayabiliyor olabilirsiniz ve istemciler ek yanıt özniteliklerini yoksayabilir.

Ancak, bazen bir hizmet API 'sinde büyük ve uyumsuz değişiklikler yapmanız gerekebilir. İstemci uygulamaları veya hizmetleri hemen yeni sürüme yükseltmeye zorlamadığından, bir hizmetin bazı bir süre için önceki API sürümlerini desteklemesi gerekir. REST gibi HTTP tabanlı bir mekanizma kullanıyorsanız, API sürüm numarasını URL 'ye veya bir HTTP üstbilgisine eklemek bir yaklaşım olur. Daha sonra aynı hizmet örneğinde hizmetin her iki sürümünü de uygulamayla veya her bir API 'nin bir sürümünü ele alan farklı örnekler dağıtmaya karar verebilirsiniz. Bunun için iyi bir yaklaşım, farklı uygulama sürümlerini bağımsız işleyicilere ayırmak için [Ortalama deseninin](https://en.wikipedia.org/wiki/Mediator_pattern) (örneğin, [mediaTR kitaplığı](https://github.com/jbogard/MediatR)).

Son olarak, bir REST mimarisi kullanıyorsanız, hizmetlerinizin sürümü oluşturmaya yönelik en iyi çözüm ve gelişmeye yönelik API 'Ler için [hiper medya](https://www.infoq.com/articles/mark-baker-hypermedia) kullanılır.

## <a name="additional-resources"></a>Ek kaynaklar

- **Scott Hanselman. ASP.NET Core daha fazla Web API sürümü oluşturma kolaylaştırıldı** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Yeniden bir Web API 'sinin sürümü oluşturma** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy Fielding. Sürüm oluşturma, hiper medya ve REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
>[Önceki](asynchronous-message-based-communication.md) 
> [Sonraki](microservices-addressability-service-registry.md)
