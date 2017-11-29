---
title: "MSMQ Tümleştirme Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 49bde10ed614a97752f0a378e16c548eb605db32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="msmq-integration-transport"></a>MSMQ Tümleştirme Taşıma
Bu konu, MSMQ tümleştirme taşıma tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|İleti boyutları bir tamsayı değeri aralığında olması gerekir böylece bu Fabrika iletileri arabelleğe alır.|  
|MsmqByteArrayBodyExpected|Belirtilen seri hale getirme biçimi ve MSMQ İleti gövdesini arasında bir uyuşmazlığı oluştu. İleti gönderilen veya alınan. Seri hale getirme biçimi ByteArray türü byte [] MSMQ iletinin gövdesi gerektirir.|  
|MsmqCannotDeserializeActiveXMessage|ActiveX seri hale getirme hatası oluştu. İleti gönderilen veya alınan. Belirtilen değişken türü gövdesi için gerçek MSMQ İleti gövdesi eşleşmiyor.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|İleti özelliklerini uyumsuz. İleti gönderilen veya alınan. BodyType ileti özelliği olamaz ActiveX seri hale getirme biçimi kullanıyorsa belirtildi.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|MsmqIntegrationBinding doğrulaması başarısız oldu. Hizmet uç noktası başlatılamıyor. Belirtilen bağlama yöntem imzası belirtilen sözleşmede belirtilen hizmet işlemi desteklemiyor. MsmqIntegrationBinding kullanmak için hizmet işlemi düzeltin.|  
|MsmqInvalidTypeDeserialization|Seri hale getirme biçimi tanınamıyor ActiveX seri hale getirme başarısız oldu. İleti gönderilen veya alınan.|  
|MsmqInvalidTypeSerialization|Değişken türü tanınmıyor. ActiveX seri hale getirilemedi. İleti gönderilen veya alınan. Belirtilen değişken türü desteklenmiyor.|  
|MsmqStreamBodyExpected|Seri hale getirme biçimi ile gövde içerik arasındaki uyumsuzluk. İleti gönderilen veya alınan. Yalnızca bir gövde türü akışın gönderilebilir veya akış serileştirme modu kullanılarak alınan.|
