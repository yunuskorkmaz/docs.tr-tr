---
description: 'Hakkında daha fazla bilgi edinin: 119-WorkflowInstanceUpdatedRecord'
title: 119 - WorkflowInstanceUpdatedRecord
ms.date: 03/30/2017
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
ms.openlocfilehash: e59bbe81d548fccb0d44d6f8c1b442ee6ad685f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703204"
---
# <a name="119---workflowinstanceupdatedrecord"></a>119 - WorkflowInstanceUpdatedRecord

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|119|  
|Anahtar sözcükler|HealthMonitoring, WFTracking|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir iş akışı örneği güncelleştirildiği zaman ETW izleme katılımcısı tarafından yayınlanır.  
  
## <a name="message"></a>İleti  

 TrackRecord = WorkflowInstanceUpdatedRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, ek açıklama = %8, ProfileName = %9  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|ActivityDefinitionId|xs: String|İş akışındaki Kök etkinliğin adı|  
|Durum|xs: String|Iş akışının geçerli durumu.|  
|OriginalDefinitionIdentity|xs: String|Özgün iş akışı Tanım kimliği|  
|UpdatedDefinitionIdentity|xs: String|Güncelleştirilmiş iş akışı Tanım kimliği|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar. Değerler, \<items> \< item name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> . Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|WorkflowDefinitionIdentity|xs: String|İş akışı Tanım kimliği|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
