---
title: Dayanıklı Uygulamalar Uygulama
description: Mikro hizmet mimarisinde çekirdek kavram olan esnekliği hakkında bilgi edinin. Geçici hataların, gerçekleştikleri için düzgün bir şekilde nasıl işleneceğini bilmeniz gerekir.
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296062"
---
# <a name="implement-resilient-applications"></a>Esnek uygulamalar uygulama

*Mikro hizmetiniz ve bulut tabanlı uygulamalarınız, sonunda tamamen gerçekleşmeyecek olan kısmi hataların ayracına sahip olmalıdır. Uygulamanızı bu kısmi hatalara dayanıklı olacak şekilde tasarlamanız gerekir.*

Dayanıklılık, hatalardan kurtulmakta ve çalışmaya devam edebilmesidir. Arızaların oluşması ve bu durum, kapalı kalma süresi veya veri kaybını önleyen bir şekilde hatalara neden olacağı gerçeğini kabul etmeyle ilgili değildir. Dayanıklılık amacı, bir hatadan sonra uygulamayı tam çalışır duruma döndürmektir.

Mikro hizmet tabanlı bir uygulama tasarlamak ve dağıtmak yeterince zor. Ancak, uygulamanızı bazı hata sıralaması belirli bir ortamda çalışır durumda tutmanız gerekir. Bu nedenle, uygulamanız dayanıklı olmalıdır. Ağ kesintileri veya düğümler ya da bulutta kilitlenen VM 'Ler gibi kısmi hatalarla başa çıkabilmelidir. Küme içindeki farklı bir düğüme taşınan mikro hizmetler (kapsayıcılar) bile uygulama içinde aralıklı kısa hatalara neden olabilir.

Uygulamanızın birçok ayrı bileşeni de sistem durumu izleme özellikleri de içermelidir. Bu bölümdeki yönergeleri izleyerek, artma geçici kapalı kalma süresi veya karmaşık ve bulut tabanlı dağıtımlarda oluşan normal hiccups içinde sorunsuz şekilde çalışan bir uygulama oluşturabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)İleri
>[](handle-partial-failure.md)
