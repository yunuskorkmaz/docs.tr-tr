---
title: WCF geliştiricileri için ek-gRPC
description: Modern mikro hizmet mimarilerinde dağıtılmış işlemlerin ve bunların uygulamalarının tartışılması.
ms.date: 09/02/2019
ms.openlocfilehash: f60899463a13e9f740f6ae63150d18eab3069124
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165864"
---
# <a name="appendix-a---transactions"></a>Ek A-Işlemler

Windows Communication Foundation (WCF) dağıtılmış işlemleri destekler ve birden çok hizmet arasında Atomik işlemler gerçekleştirmenize olanak tanır. Bu işlevsellik, [Microsoft Dağıtılmış işlem Düzenleyicisi](/previous-versions/windows/desktop/ms684146(v=vs.85))tabanlıdır.

Daha yeni mikro hizmetler yataysa, bu tür otomatik dağıtılmış işlem işleme mümkün değildir. İlişkisel veritabanları, NoSQL veri depoları ve mesajlaşma sistemleri dahil olmak üzere çok sayıda farklı teknoloji vardır. Tek bir ortamda kullanımda olan işletim sistemleri, programlama dilleri ve çerçevelerin bir karışımı de olabilir.

WCF dağıtılmış işlem, [iki aşamalı işleme (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol)olarak bilinen işlemin bir uygulamasıdır. Hizmetler genelinde iletileri koordine ederek, her bir hizmette açık işlemler oluşturarak ve başarılı veya başarısız olmasına bağlı olarak işleme veya geri alma iletileri göndererek, 2PC işlemlerini el ile uygulayabilirsiniz. Ancak, 2PC 'yi yönetme bölümünde yer alan karmaşıklık, sistemler geliştikçe üstel olarak artabilir. Açık işlemler, performansı olumsuz etkileyebilecek veya daha kötü bir hizmet kilitlenmesine neden olabilecek veritabanı kilitlerini tutar.

Mümkünse, dağıtılmış işlemlerden tamamen kaçınmak en iyisidir. İki veri öğesi atomik güncelleştirmeler gerektirecek şekilde bağlanmışsa, bunları aynı hizmetle işlemeyi göz önünde bulundurun. Bu atomik değişiklikleri, bu hizmete tek bir istek veya ileti kullanarak uygulayın.

Bu mümkün değilse, tek bir alternatif, [Saga deseninin](https://microservices.io/patterns/data/saga.html)kullanılması olabilir. Bir Saga 'de güncelleştirmeler sırayla işlenir; Her güncelleştirme başarılı olduğu için, bir sonraki tetiklenir. Bu Tetikleyiciler hizmetten hizmete yayılamaz veya bir Saga Düzenleyicisi veya Orchestrator tarafından yönetilebilir. İşlem sırasında herhangi bir noktada bir güncelleştirme başarısız olursa, güncelleştirmelerini zaten tamamlamış olan hizmetler bunları tersine çevirmek için özel mantık uygular.

Diğer bir seçenek de, [.net mikro hizmetleri e-defterinde](../microservices/microservice-ddd-cqrs-patterns/index.md)açıklandığı gibi etki alanı odaklı TASARıM (DDD) ve komut/sorgu sorumluluğu ayrımı (CQRS) kullanmaktır. Özellikle, etki alanı olaylarının veya [olay](https://martinfowler.com/eaaDev/EventSourcing.html) kaynağını kullanmanın kullanılması, güncelleştirmelerin sürekli olarak uygulanmadığından emin olmanıza yardımcı olabilir.

>[!div class="step-by-step"]
>[Önceki](application-performance-management.md)
