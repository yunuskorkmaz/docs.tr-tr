---
description: 'Hakkında daha fazla bilgi edinin: 118-Workflowınstanceunhandledexceptionrecordwithıd'
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: 9d39afb95db8a393b967d590ee37e9f3f2529ffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703230"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|118|  
|Anahtar sözcükler|HealthMonitoring, WFTracking|  
|Level|Hata|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir iş akışı örneği Workflowunhandledexceptionrecord ' i yayıyorsa ETW izleme katılımcısı tarafından yayılır.  
  
## <a name="message"></a>İleti  

 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, özel durum = %9, ek açıklama = %10, ProfileName = %11, WorkflowDefinitionIdentity = %12  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|ActivityDefinitionId|xs: String|İş akışındaki Kök etkinliğin adı|  
|Kaynak|xs: String|Hatalı kaynak etkinliğin adı, unhandledException ile sonuçlanır|  
|ID|xs: String|Hata kaynağı etkinliğinin etkinlik kimliği|  
|SourceInstanceId|xs: String|Hata kaynağı etkinliğinin etkinlik örneği kimliği|  
|SourceTypeName|xs: String|Hatalı olan kaynak etkinlik türü adı, unhandledException ile sonuçlanır|  
|Özel durum|xs: String|İşlenmeyen özel durum için özel durum ayrıntıları|  
|Durum|xs: String|Iş akışının geçerli durumu.|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar. Değerler, \<items> \< item name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> . Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|WorkflowDefinitionIdentity|xs: String|İş akışı Tanım kimliği|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
