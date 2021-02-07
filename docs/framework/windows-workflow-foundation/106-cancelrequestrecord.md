---
description: 'Hakkında daha fazla bilgi edinin: 106-CancelRequestRecord'
title: 106 - CancelRequestRecord
ms.date: 03/30/2017
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
ms.openlocfilehash: a5d65ef8606821dc8aa7b64b36498b343ff986e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667665"
---
# <a name="106---cancelrequestrecord"></a>106 - CancelRequestRecord

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|106|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir iş akışı örneği içindeki bir etkinlik CancelRequestedRecord olarak yayıyorsa ETW izleme katılımcısı tarafından yayılır.  
  
## <a name="message"></a>İleti  

 TrackRecord = CancelRequestedRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ad = %4, ActivityID = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = %10, ChildActivityTypeName = %11, ek açıklamalar = %12, ProfileName = %13  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|Name|xs: String|İptal işlemini isteyen etkinliğin adı|  
|ActivityId|xs: String|İptal işlemini isteyen etkinliğin kimliği|  
|ActivityInstanceId|xs: String|İptal işlemini isteyen etkinliğin örnek kimliği|  
|ActivityTypeName|xs: String|İptal işlemini isteyen etkinliğin türü|  
|ChildActivityName|xs: String|İptal edilen etkinliğin adı|  
|ChildActivityId|xs: String|İptal edilen etkinliğin kimliği|  
|ChildActivityInstanceId|xs: String|İptal edilen etkinliğin örnek kimliği|  
|ChildActivityTypeName|xs: String|İptal edilen etkinliğin türü|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örneği: ' Default Web site/Hesaplatokıpplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice ' olarak tanımlanmıştır|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
