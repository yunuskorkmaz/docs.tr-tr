---
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: eb69fc4760cd89294e24680b5aab83fcd058feb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009883"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|118|  
|anahtar sözcükler|Ögesi, WFTracking|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, bir iş akışı örneği WorkflowInstanceUnhandledExceptionRecord içerilip ETW İzleme katılımcı tarafından yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord WorkflowInstanceUnhandledExceptionRecord, InstanceId = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, özel durum = %9, ek açıklamalar = % 10, ProfileName = % 11, WorkflowDefinitionIdentity = % 12  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|İş akışı örnek kimliği|  
|Kayıt numarası|xs:long|Yayılan kaydın sıra numarası|  
|eventTime|xs:dateTime|Olay gösteriliyordu, UTC zamanı|  
|activityDefinitionId|xs:string|İş akışı içinde Kök etkinlik adı|  
|SourceName|xs:string|İçinde unhandledException kaynaklanan hatalı kaynak etkinliği adı|  
|SourceId|xs:string|Hata kaynağı etkinliğin etkinlik kimliği|  
|SourceInstanceId|xs:string|Hata kaynak etkinliği etkinlik örneği kimliği|  
|SourceTypeName|xs:string|İçinde unhandledException kaynaklanan hatalı kaynak etkinlik türü adı|  
|Özel Durum|xs:string|İşlenmeyen özel durum için özel durum ayrıntıları|  
|Durum|xs:string|İş akışının geçerli durumu.|  
|Ek Açıklamalar|xs:string|Bu olay için eklenen ek açıklamalar. Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</item > \< /öğeler >. Dize içeriyorsa hiçbir ek açıklama belirtilirse \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olayı bırakarak ek açıklamalar ve ek açıklama değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.|  
|profileName|xs:string|Adı veya yayılan bu olay ile sonuçlanan bir izleme profili|  
|WorkflowDefinitionIdentity|xs:string|İş akışı tanımı kimliği|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
