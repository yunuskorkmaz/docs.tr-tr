---
description: 'Daha fazla bilgi edinin: MSMQ tümleştirme taşıma'
title: MSMQ Tümleştirme Taşıma
ms.date: 03/30/2017
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
ms.openlocfilehash: a9d47a3a15778bdeb52d2a9ab38610803448de4f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686407"
---
# <a name="msmq-integration-transport"></a>MSMQ Tümleştirme Taşıma

Bu konu, MSMQ tümleştirme aktarımı tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Bu fabrika iletileri arabelleğe alır, bu nedenle ileti boyutları bir tamsayı değeri aralığında olmalıdır.|  
|Msmqbytearraybodybekleniyordu|Belirtilen serileştirme biçimi ile MSMQ iletisinin gövdesi arasında uyuşmazlık oluştu. İleti gönderilemiyor veya alınamıyor. ByteArray seri hale getirme biçimi, MSMQ iletisinin gövdesinin Byte [] türünde olmasını gerektirir.|  
|MsmqCannotDeserializeActiveXMessage|Bir ActiveX serileştirme hatası oluştu. İleti gönderilemiyor veya alınamıyor. Gövde için belirtilen değişken türü, gerçek MSMQ ileti gövdesi ile eşleşmiyor.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|İletinin özellikleri eşleşmiyor. İleti gönderilemiyor veya alınamıyor. ActiveX serileştirme biçimi kullanılıyorsa, BodyType iletisi özelliği belirtilemez.|  
|Msmqınvalidserviceoperationformsmqıntegrationbinding|MsmqIntegrationBinding doğrulaması başarısız oldu. Hizmet uç noktası başlatılamıyor. Belirtilen bağlama belirtilen sözleşmede belirtilen hizmet işlemi için yöntem imzasını desteklemiyor. MsmqIntegrationBinding 'i kullanmak için hizmet işlemini düzeltin.|  
|Msmqınvalidtypedeserialization|Serileştirme biçimi tanınamadığından, ActiveX serileştirme başarısız oldu. İleti gönderilemiyor veya alınamıyor.|  
|Msmqınvalidtypeserialization|Değişken türü tanınmıyor. ActiveX serileştirme başarısız oldu. İleti gönderilemiyor veya alınamıyor. Belirtilen değişken türü desteklenmiyor.|  
|Msmqstreambodybekleniyordu|Serileştirme biçimi ve gövde içeriği arasında uyuşmazlık var. İleti gönderilemiyor veya alınamıyor. Akış serileştirme modu kullanılarak yalnızca akış türünde bir gövde gönderilebilir veya alınabilir.|
