---
description: 'Hakkında daha fazla bilgi edinin: 102-WorkflowInstanceAbortedRecord'
title: 102 - WorkflowInstanceAbortedRecord
ms.date: 03/30/2017
ms.assetid: bde4378d-4eea-4907-aaf2-c1a2bc770a37
ms.openlocfilehash: 2fd192af1624618a2800843ad58a1fc65d5f86b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792862"
---
# <a name="102---workflowinstanceabortedrecord"></a>102 - WorkflowInstanceAbortedRecord

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|102|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir iş akışı örneği WorkflowInstanceAbortedRecord yaydığı zaman ETW izleme katılımcısı tarafından yayılır.  
  
## <a name="message"></a>İleti  

 TrackRecord = WorkflowInstanceAbortedRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, ek açıklama = %6, ProfileName = %7  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|ActivityDefinitionId|xs: String|İş akışındaki Kök etkinliğin adı|  
|Nedeni|xs: String|İş akışının durdurulduğu neden|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örneği: ' Default Web site/Hesaplatokıpplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice ' olarak tanımlanmıştır|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
