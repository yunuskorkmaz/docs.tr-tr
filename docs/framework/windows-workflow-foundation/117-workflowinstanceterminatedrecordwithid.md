---
description: 'Hakkında daha fazla bilgi edinin: 117-Workflowınstancesonlandırıcıkayıt Withıd'
title: 117 - WorkflowInstanceTerminatedRecordWithId
ms.date: 03/30/2017
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
ms.openlocfilehash: d57940801cd9850136355a9ad4f91ba7c44fd5b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703243"
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a>117 - WorkflowInstanceTerminatedRecordWithId

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|117|  
|Anahtar sözcükler|HealthMonitoring, WFTracking|  
|Level|Hata|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir iş akışı örneği Workflowsonlandırmış kaydı yaydığı zaman ETW izleme katılımcısı tarafından yayınlanır.  
  
## <a name="message"></a>İleti  

 TrackRecord = Workflowınstancesonlandırıo kaydı, InstanceId = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, ek açıklama = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
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
