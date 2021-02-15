---
title: Esnek uygulamalar uygulama
description: Mikro hizmet mimarisinde çekirdek kavram olan esnekliği hakkında bilgi edinin. Meydana geldiğinde geçici hataların düzgün bir şekilde nasıl işleneceğini bilmeniz gerekir.
ms.date: 01/30/2020
ms.openlocfilehash: 3ed4474eaa1225e80f05db86965e4ba53b5d2301
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429331"
---
# <a name="implement-resilient-applications"></a>Esnek uygulamalar uygulama

*Mikro hizmetiniz ve bulut tabanlı uygulamalarınız, sonunda tamamen gerçekleşmeyecek olan kısmi hataların ayracına sahip olmalıdır. Uygulamanızı bu kısmi hatalara dayanıklı olacak şekilde tasarlamanız gerekir.*

Dayanıklılık, hatalardan kurtulmakta ve çalışmaya devam edebilmesidir. Arızaların oluşması ve bu durum, kapalı kalma süresi veya veri kaybını önleyen bir şekilde hatalara neden olacağı gerçeğini kabul etmeyle ilgili değildir. Dayanıklılık amacı, bir hatadan sonra uygulamayı tam çalışır duruma döndürmektir.

Mikro hizmet tabanlı bir uygulama tasarlamak ve dağıtmak yeterince zor. Ancak, uygulamanızı bazı hata sıralaması belirli bir ortamda çalışır durumda tutmanız gerekir. Bu nedenle, uygulamanız dayanıklı olmalıdır. Ağ kesintileri veya düğümler ya da bulutta kilitlenen VM 'Ler gibi kısmi hatalarla başa çıkabilmelidir. Küme içindeki farklı bir düğüme taşınan mikro hizmetler (kapsayıcılar) bile uygulama içinde aralıklı kısa hatalara neden olabilir.

Uygulamanızın birçok ayrı bileşeni de sistem durumu izleme özellikleri de içermelidir. Bu bölümdeki yönergeleri izleyerek, artma geçici kapalı kalma süresi veya karmaşık ve bulut tabanlı dağıtımlarda oluşan normal hiccups içinde sorunsuz şekilde çalışan bir uygulama oluşturabilirsiniz.

>[!IMPORTANT]
> eShopOnContainer, sürüm 3.0.0 kadar [yazılan istemcileri](./use-httpclientfactory-to-implement-resilient-http-requests.md) kullanarak dayanıklılık uygulamak Için [Polly kitaplığını](https://thepollyproject.azurewebsites.net/) kullanıyor vardı.
>
> Release 3.0.0 ile başlayarak, HTTP çağrıları dayanıklılığı bir [Kkerd ağı](https://linkerd.io/)kullanılarak, bir Kubernetes kümesi içindeki yeniden denemeleri, koddaki kaygıları işlemeye gerek kalmadan bir saydam ve yapılandırılabilir biçimde işler.
>
> Polly kitaplığı, Hizmetleri başlatırken özel olarak esnekliği veritabanı bağlantılarına eklemek için de kullanılır.

>[!WARNING]
> Bu bölümdeki tüm kod örnekleri, Linkerd kullanılmadan önce geçerlidir ve geçerli gerçek kodu yansıtacak şekilde güncellenmez. Bu nedenle, bu bölümün bağlamında mantıklı olurlar.

>[!div class="step-by-step"]
>[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) 
> [Sonraki](handle-partial-failure.md)
