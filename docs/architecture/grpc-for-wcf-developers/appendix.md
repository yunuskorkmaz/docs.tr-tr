---
title: WCF geliştiricileri için ek-gRPC
description: Modern mikro hizmet mimarilerinde dağıtılmış işlemlerin ve bunların uygulamalarının tartışılması.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 10c4e77794c5ffe1aa6d5a629ce0b6cdf92f4ada
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184619"
---
# <a name="appendix-a---transactions"></a>Ek A-Işlemler

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Windows Communication Foundation (WCF) desteklenen dağıtılmış işlemler, birden çok hizmet arasında atomik işlemlerin gerçekleştirilmesine izin verir. Bu işlevsellik [Microsoft Dağıtılmış işlem Düzenleyicisi](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85))tabanlıdır.

Modern mikro hizmetler dikey penceresinde bu tür otomatik dağıtılmış işlem işleme mümkün değildir. Birçok farklı teknolojiden, ilişkisel veritabanları, NoSQL veri depoları ve mesajlaşma sistemleri dahil olmak üzere, tek bir ortamda kullanılabilecek işletim sistemleri, programlama dilleri ve çerçeveler dahil olmak üzere çok sayıda farklı teknoloji vardır.

WCF dağıtılmış işlemi, [iki aşamalı işleme (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol)olarak bilinen işlemin bir uygulamasıdır. Hizmetler genelinde iletileri koordine ederek, her bir hizmette açık işlemler oluşturarak ve başarı veya başarısızlık durumuna bağlı olarak "COMMIT" veya "Rollback" iletileri göndererek, 2PC işlemlerini el ile uygulamak mümkündür. Ancak, 2PC 'yi yönetmek için kullanılan karmaşıklık, sistem geliştikçe üstel olarak artabilir ve açık işlemler, performansı olumsuz yönde etkileyebilecek veya daha kötü bir hizmet kilitlenmesine neden olabilecek veritabanı kilitlerini tutar.

Mümkünse, dağıtılmış işlemlerden tamamen kaçınmak en iyisidir. İki veri öğesi atomik güncelleştirmeler gerektirecek şekilde bağlanmışsa, bunları aynı hizmetle işlemeyi ve bu hizmet için tek bir istek veya ileti kullanarak bu atomik değişiklikleri uygulamayı düşünün.

Bu mümkün değilse, tek bir alternatif, [Saga deseninin](https://microservices.io/patterns/data/saga.html)kullanılması olabilir. Bir Saga 'de güncelleştirmeler sırayla işlenir; Her güncelleştirme başarılı olduğu için bir sonraki tetiklenir. Bu Tetikleyiciler hizmetten hizmete yayılamaz veya bir Saga Düzenleyicisi veya "Orchestrator" tarafından yönetilebilir. İşlem sırasında herhangi bir noktada bir güncelleştirme başarısız olursa, güncelleştirmelerini zaten tamamlamış olan hizmetler bunları tersine çevirmek için özel mantık uygular.

Diğer bir seçenek de, [.net mikro hizmetleri e-defterinde](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)açıklandığı gibi etki alanı odaklı TASARıM (DDD) ve komut/sorgu sorumluluğu ayrımı (CQRS) kullanmaktır. Özellikle, etki alanı olaylarının veya [olay](https://martinfowler.com/eaaDev/EventSourcing.html) kaynağını kullanmanın kullanılması, güncelleştirmelerin hemen&mdash;&mdash;uygulanmadığından tutarlı olmasını sağlamaya yardımcı olabilir.

>[!div class="step-by-step"]
>[Önceki](application-performance-management.md)
