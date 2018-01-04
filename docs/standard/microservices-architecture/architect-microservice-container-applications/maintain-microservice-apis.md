---
title: "Oluşturma, Gelişmekte olan ve sürüm oluşturma mikro hizmet API'leri ve sözleşmeler"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Oluşturma, Gelişmekte olan ve sürüm oluşturma mikro hizmet API'leri ve sözleşmeler"
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
ms.openlocfilehash: 3aaa7eaa8bc535874369cf08414f2211cae1bed9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Oluşturma, Gelişmekte olan ve sürüm oluşturma mikro hizmet API'leri ve sözleşmeler

Mikro hizmet API, hizmet ve istemcileri arasında bir sözleşmedir. Yalnızca çok önemli bir sözleşmedir neden olan API sözleşmesinin bozmadığını varsa bir mikro hizmet bağımsız olarak gelişmesi kuramaz. Sözleşme değiştirirseniz, istemci uygulamaları veya API ağ geçidi etkiler.

API tanımı yapısını hangi protokolünü kullandığınıza bağlıdır. Örneğin, ileti kullanıyorsanız (gibi [AMQP](https://www.amqp.org/)), ileti türlerini API oluşur. HTTP ve RESTful hizmetlerini kullanıyorsanız, API URL'leri ve istek ve yanıt JSON biçimleri oluşur.

Ancak, ilk sözleşme hakkında Düşünceli olsa bile, bir hizmeti API'si zamanla değiştirmeniz gerekir. Bu durumda — ve özellikle, API birden çok istemci uygulamaları tarafından kullanılan ortak bir API olduğunda — tüm istemcilerin yeni API sözleşmesine yükseltmek için genellikle zorlayamaz. Genellikle, aynı anda bir hizmet sözleşmesini hem eski hem de yeni sürümlerini çalıştıran bir şekilde bir hizmetin yeni sürümler artımlı olarak dağıtmanız gerekir. Bu nedenle, bir strateji, hizmet sürümü oluşturma için önemlidir.

API değişiklikleri API'nize öznitelikleri veya parametrelerini eklerseniz gibi küçük olduğunda, daha eski bir API kullanan istemciler geçin ve hizmet yeni sürümü ile çalışma. Gerekli olan eksik öznitelikleri için varsayılan değerler sağlamak mümkün olabilir ve istemcilerin ek yanıt öznitelikleri yoksay olabilir.

Ancak, bazen büyük uyumsuz bir hizmet API değişiklik yapmak ve gerekir. İstemci uygulamaları veya hizmetleri hemen en yeni sürüme yükseltmek için zorlamak kuramamış olabilir çünkü bir hizmeti belirli bir süre için API eski sürümleri desteklemesi gerekir. Bir HTTP tabanlı mekanizması REST gibi kullanıyorsanız, bir URL veya bir HTTP üstbilgisi içine API sürüm numarası katıştırmak için yaklaşımdır. Sonra hizmet aynı anda aynı hizmet örneği içinde her iki sürümü uygulama veya her bir API sürümü işlemek farklı örnekleri dağıtma arasında karar verebilirsiniz. Bunun için iyi bir yaklaşımdır [Dünyası düzeni](https://en.wikipedia.org/wiki/Mediator_pattern) (örneğin, [MediatR Kitaplığı](https://github.com/jbogard/MediatR)) bağımsız işleyicileri farklı uygulama sürümleri aynı şekilde.

Son olarak, bir REST mimarisi kullanıyorsanız [iletilir](https://www.infoq.com/articles/mark-baker-hypermedia) hizmetlerinizi sürüm oluşturma için en iyi çözüm olduğunu ve evolvable API'leri izin verme.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Scott Hanselman. ASP.NET Core RESTful Web API'si sürüm kolaylaştırılmış**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

-   **Sürüm oluşturma bir RESTful web API'si**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Sürüm oluşturma, iletilir ve REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning>


>[!div class="step-by-step"]
[Önceki] (zaman uyumsuz-ileti-tabanlı-communication.md) [sonraki] (mikro-çözümlenebilme-service-registry.md)
