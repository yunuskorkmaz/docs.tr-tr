---
title: WCF geliştiricileri için ek-gRPC
description: Modern mikro hizmet mimarilerinde dağıtılmış işlemlerin ve bunların uygulamalarının tartışılması.
ms.date: 09/02/2019
ms.openlocfilehash: 9931681727f921e007c2f80852ad0e69cd7288de
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711464"
---
# <a name="appendix-a---transactions"></a>Ek A-Işlemler

Windows Communication Foundation (WCF) dağıtılmış işlemleri destekler ve birden çok hizmet arasında Atomik işlemler gerçekleştirmenize olanak tanır. Bu işlevsellik, [Microsoft Dağıtılmış işlem Düzenleyicisi](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85))tabanlıdır.

Daha yeni mikro hizmetler yataysa, bu tür otomatik dağıtılmış işlem işleme mümkün değildir. İlişkisel veritabanları, NoSQL veri depoları ve mesajlaşma sistemleri dahil olmak üzere çok sayıda farklı teknoloji vardır. Tek bir ortamda kullanımda olan işletim sistemleri, programlama dilleri ve çerçevelerin bir karışımı de olabilir.

WCF dağıtılmış işlem, [iki aşamalı işleme (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol)olarak bilinen işlemin bir uygulamasıdır. Hizmetler genelinde iletileri koordine ederek, her bir hizmette açık işlemler oluşturarak ve başarılı veya başarısız olmasına bağlı olarak işleme veya geri alma iletileri göndererek, 2PC işlemlerini el ile uygulayabilirsiniz. Ancak, 2PC 'yi yönetme bölümünde yer alan karmaşıklık, sistemler geliştikçe üstel olarak artabilir. Açık işlemler, performansı olumsuz etkileyebilecek veya daha kötü bir hizmet kilitlenmesine neden olabilecek veritabanı kilitlerini tutar.

Mümkünse, dağıtılmış işlemlerden tamamen kaçınmak en iyisidir. İki veri öğesi atomik güncelleştirmeler gerektirecek şekilde bağlanmışsa, bunları aynı hizmetle işlemeyi göz önünde bulundurun. Bu atomik değişiklikleri, bu hizmete tek bir istek veya ileti kullanarak uygulayın.

Bu mümkün değilse, tek bir alternatif, [Saga deseninin](https://microservices.io/patterns/data/saga.html)kullanılması olabilir. Bir Saga 'de güncelleştirmeler sırayla işlenir; Her güncelleştirme başarılı olduğu için, bir sonraki tetiklenir. Bu Tetikleyiciler hizmetten hizmete yayılamaz veya bir Saga Düzenleyicisi veya Orchestrator tarafından yönetilebilir. İşlem sırasında herhangi bir noktada bir güncelleştirme başarısız olursa, güncelleştirmelerini zaten tamamlamış olan hizmetler bunları tersine çevirmek için özel mantık uygular.

Diğer bir seçenek de, [.net mikro hizmetleri e-defterinde](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)açıklandığı gibi etki alanı odaklı TASARıM (DDD) ve komut/sorgu sorumluluğu ayrımı (CQRS) kullanmaktır. Özellikle, etki alanı olaylarının veya [olay](https://martinfowler.com/eaaDev/EventSourcing.html) kaynağını kullanmanın kullanılması, güncelleştirmelerin sürekli olarak uygulanmadığından emin olmanıza yardımcı olabilir.

>[!div class="step-by-step"]
>[Öncekini](application-performance-management.md)
