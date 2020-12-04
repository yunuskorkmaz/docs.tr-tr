---
title: Çalışma zamanı olayları
description: ETW, LTTng veya EventPipe ile kullanılabilen .NET Runtime (CoreCLR) tarafından yayılan Tanılama olaylarını gözden geçirin.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96589997"
---
# <a name="net-runtime-events"></a>.NET çalışma zamanı olayları

.NET çalışma zamanı (CoreCLR),, ve gibi çeşitli mekanizmalarla tüketilebilen .NET uygulamanızla ilgili sorunları tanılamak için kullanılabilecek çeşitli olayları yayar `ETW` `LTTng` `EventPipe` .

Bu belge .NET Core çalışma zamanı tarafından tetiklenen olaylara başvuru görevi görür.

.NET Framework çalışma zamanı olayları için bkz. [CLR ETW olayları](../../framework/performance/clr-etw-events.md).

## <a name="in-this-section"></a>Bu bölümde

[Çekişme olayları](runtime-contention-events.md)\
Bu olaylar izleyici kilitleme çekişmeleri hakkında bilgi toplar.

[Çöp toplama olayları](runtime-garbage-collection-events.md)\
Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar. Çöp toplamanın kaç kez gerçekleştirildiğini belirleme, çöp toplama sırasında ne kadar bellek serbest bırakılmış vb. gibi tanılama ve hata ayıklama konusunda yardımcı olurlar.

[Özel durum olayları](runtime-exception-events.md)\
Bu çalışma zamanı olayları, oluşturulan özel durumlarla ilgili bilgileri yakalar.

[Birlikte çalışma olayları](runtime-interop-events.md)\
Bu çalışma zamanı olayları ortak ara dil (CıL) saplama oluşturma hakkındaki bilgileri yakalar.

[Yükleyici ve Ciltçi olayları](runtime-loader-binder-events.md)\
Bu olaylar derlemeleri ve modülleri yükleme ve kaldırma ile ilgili bilgiler toplar.

[Yöntem olayları](runtime-method-events.md)\
Bu olaylar yöntemlere özgü bilgiler toplar. Bu olayların yükü sembol çözümlemesi için gereklidir. Ayrıca, bu olaylar yöntemin kaç kez çağrıldığı gibi yararlı bilgiler sağlar.

[İş parçacığı olayları](runtime-thread-events.md)\
Bu olaylar, çalışan ve g/ç iş parçacıkları hakkında bilgi toplar.

[Tür olayları](runtime-type-events.md)\
Bu olaylar tür sistemi hakkında bilgi toplar.
