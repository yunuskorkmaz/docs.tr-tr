---
title: Esnek uygulamaları uygulayın
description: Mikro hizmetler mimarisinde temel bir kavram olan esneklik hakkında bilgi edinin. Geçici hatalar oluştuğunda incelikle nasıl işleyeceğinizi bilmeniz gerekir.
ms.date: 01/30/2020
ms.openlocfilehash: 46276a6b9b36a494bfae657275692ca9d5554d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78847238"
---
# <a name="implement-resilient-applications"></a>Esnek uygulamaları uygulayın

*Mikro hizmet ve bulut tabanlı uygulamalarınız, eninde sonunda kesinlikle ortaya çıkacak kısmi hataları benimsemelidir. Uygulamanızı bu kısmi hatalara karşı dirençli olacak şekilde tasarlamanız gerekir.*

Esneklik, başarısızlıklardan kurtulma ve çalışmaya devam etme yeteneğidir. Bu hatalardan kaçınmakla ilgili değil, hataların gerçekleşeceği gerçeğini kabul etmek ve bunlara kapalı kalma süresini veya veri kaybını önleyecek şekilde yanıt vermektir. Esnekliğin amacı, bir hatadan sonra uygulamayı tam olarak işleyen bir duruma döndürmektir.

Mikro hizmetler tabanlı bir uygulama tasarlamak ve dağıtmak için yeterince zor. Ancak, uygulamanızın bir tür hatanın kesin olduğu bir ortamda çalışmasını da engellemeniz gerekir. Bu nedenle, uygulamanız esnek olmalıdır. Ağ kesintileri veya düğümler veya bulutta çöken VM'ler gibi kısmi hatalarla başa çıkacak şekilde tasarlanmalıdır. Bir küme içinde farklı bir düğüme taşınan mikro hizmetler (kapsayıcılar) bile uygulama içinde aralıklı kısa arızalara neden olabilir.

Uygulamanızın birçok bireysel bileşeni, sistem durumu izleme özelliklerini de dahil etmelidir. Bu bölümdeki yönergeleri izleyerek, geçici kapalı kalma süresine veya karmaşık ve bulut tabanlı dağıtımlarda oluşan normal hıçkırıklara rağmen sorunsuz çalışabilen bir uygulama oluşturabilirsiniz.

>[!IMPORTANT]
> eShopOnContainer, [Polly kitaplığını](http://www.thepollyproject.org/) kullanarak 3.0.0 sürümüne kadar [Typed Clients'ı](./use-httpclientfactory-to-implement-resilient-http-requests.md) kullanarak esneklik uygulamaktadır.
>
> Sürüm 3.0.0 ile başlayarak, HTTP çağrıları esneklik bir [Linkerd örgü](https://linkerd.io/)kullanılarak uygulanır , şeffaf ve yapılandırılabilir bir şekilde retries işler, bir Kubernetes küme içinde, kodbu endişeleri işlemek zorunda kalmadan.
>
> Polly kitaplığı, özellikle hizmetleri başlatırken veritabanı bağlantılarına esneklik eklemek için hala kullanılır.

>[!WARNING]
> Bu bölümdeki tüm kod örnekleri Linkerd kullanmadan önce geçerliydi ve geçerli gerçek kodu yansıtacak şekilde güncelleştirilmeyecektir. Bu yüzden bu bölümün bağlamında mantıklı.

>[!div class="step-by-step"]
>[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Sonraki](handle-partial-failure.md)
