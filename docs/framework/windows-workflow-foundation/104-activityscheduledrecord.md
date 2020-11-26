---
title: 104 - ActivityScheduledRecord
ms.date: 03/30/2017
ms.assetid: ae202178-8fb1-4646-a3aa-18beeda8ff93
ms.openlocfilehash: b2c7cbd169053188d5e84a0b8afd87c4916c87cb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238970"
---
# <a name="104---activityscheduledrecord"></a>104 - ActivityScheduledRecord

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|104|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, bir iş akışı örneği içindeki bir etkinlik ActivityScheduledRecord ' i yayıyorsa ETW izleme katılımcısı tarafından yayınlanır  
  
## <a name="message"></a>İleti  

 TrackRecord = ActivityScheduledRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ad = %4, ActivityID = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = %10, ChildActivityTypeName = %11, ek açıklamalar = %12, ProfileName = %13  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|Adı|xs: String|Alt etkinliği zamanladığı etkinliğin adı|  
|Etkinlik kimliği|xs: String|Alt etkinliği zamanladığı etkinliğin kimliği|  
|ActivityInstanceId|xs: String|Alt etkinliği zamanladığı etkinliğin örnek kimliği|  
|ActivityTypeName|xs: String|İptal işlemini isteyen etkinliğin türü|  
|ChildActivityName|xs: String|Zamanlanan etkinliğin adı|  
|ChildActivityId|xs: String|Zamanlanan etkinliğin kimliği|  
|ChildActivityInstanceId|xs: String|Zamanlanan etkinliğin örnek kimliği|  
|ChildActivityTypeName|xs: String|Zamanlanan etkinliğin türü|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örneği: ' Default Web site/Hesaplatokıpplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice ' olarak tanımlanmıştır|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
