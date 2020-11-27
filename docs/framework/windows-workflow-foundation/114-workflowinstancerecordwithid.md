---
title: 114 - WorkflowInstanceRecordWithId
ms.date: 03/30/2017
ms.assetid: 2bd8b4a1-b210-4c07-8156-f19392318c08
ms.openlocfilehash: ebeff6af6d18d2794723250bceeecd682d0af6df
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261858"
---
# <a name="114---workflowinstancerecordwithid"></a>114 - WorkflowInstanceRecordWithId

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|114|  
|Anahtar sözcükler|HealthMonitoring, WFTracking|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, bir iş akışı örneği iş akışı durumları için Workflowcerecord 'yi yayıyorsa ETW izleme katılımcısı tarafından yayılır: başlatıldı, sürdürüldü, kalıcı, boşta, silinmiş, tamamlandı, Iptal edildi, kaldırıldı, geri alındı.  
  
## <a name="message"></a>İleti  

 TrackRecord = Workflowcerecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, durum = %5, ek açıklama = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|ActivityDefinitionId|xs: String|İş akışındaki Kök etkinliğin adı|  
|Durum|xs: String|Iş akışının geçerli durumu.|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar. Değerler, \<items> \< item name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> . Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|WorkflowDefinitionIdentity|xs: String|İş akışı Tanım kimliği|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
