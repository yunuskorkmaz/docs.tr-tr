---
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: 54bbb267902fe547821d4a5580f86da944ae70cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278693"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|118|  
|Anahtar sözcükler|HealthMonitoring, WFTracking|  
|Düzey|Hata|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, bir iş akışı örneği Workflowunhandledexceptionrecord ' i yayıyorsa ETW izleme katılımcısı tarafından yayılır.  
  
## <a name="message"></a>İleti  

 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, özel durum = %9, ek açıklama = %10, ProfileName = %11, WorkflowDefinitionIdentity = %12  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
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
