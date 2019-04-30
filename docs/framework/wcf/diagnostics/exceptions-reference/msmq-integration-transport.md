---
title: MSMQ Tümleştirme Taşıma
ms.date: 03/30/2017
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
ms.openlocfilehash: 52fd98354ded57bd7d7c075d4f08ca543760e598
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777370"
---
# <a name="msmq-integration-transport"></a>MSMQ Tümleştirme Taşıma
Bu konu, MSMQ tümleştirme taşıma tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Bu fabrika, ileti boyutları bir tamsayı değer aralığında kalacak şekilde iletileri arabelleğe alır.|  
|MsmqByteArrayBodyExpected|MSMQ iletisinin gövdesi, belirtilen serileştirme biçimi arasında bir uyuşmazlığı oluştu. İleti gönderilen veya alınan. Seri hale getirme biçimi ByteArray olması byte [] türünde MSMQ iletisinin gövdesini gerektirir.|  
|MsmqCannotDeserializeActiveXMessage|Bir ActiveX serileştirme hata oluştu. İleti gönderilen veya alınan. Gerçek MSMQ İleti gövdesi için belirtilen değişken türü eşleşmiyor.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|İletinin özellikleri eşleşmiyor. İleti gönderilen veya alınan. BodyType ileti özelliği olamaz belirtilen ActiveX serileştirme biçimi kullanılır.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|MsmqIntegrationBinding doğrulaması başarısız oldu. Hizmet uç noktası başlatılamıyor. Belirtilen sözleşme belirtilen hizmet işlemi için belirtilen bağlama herhangi bir yöntem imzası desteklemez. MsmqIntegrationBinding kullanmak için hizmet işlemi düzeltin.|  
|MsmqInvalidTypeDeserialization|Seri hale getirme biçimi tanınamıyor ActiveX seri hale getirme başarısız oldu. İleti gönderilen veya alınan.|  
|MsmqInvalidTypeSerialization|Değişken türü tanınmıyor. ActiveX serileştirilemedi. İleti gönderilen veya alınan. Belirtilen değişken türü desteklenmiyor.|  
|MsmqStreamBodyExpected|Seri hale getirme biçimi ve İçerik gövdesi arasında uyuşmazlık var. İleti gönderilen veya alınan. Yalnızca bir gövde türü akışının gönderilebilir veya akış serileştirme modunu kullanarak aldı.|
