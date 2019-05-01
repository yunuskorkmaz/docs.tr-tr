---
title: 119 - WorkflowInstanceUpdatedRecord
ms.date: 03/30/2017
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
ms.openlocfilehash: 5bbda72208dd9cf38e7b8765d324129beaf3fa0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924078"
---
# <a name="119---workflowinstanceupdatedrecord"></a>119 - WorkflowInstanceUpdatedRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|119|  
|anahtar sözcükler|Ögesi, WFTracking|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı örneği güncelleştirildiğinde bu olay tarafından ETW İzleme katılımcı yayılır.  
  
## <a name="message"></a>İleti  
 TrackRecord WorkflowInstanceUpdatedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, durum = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, ek açıklamalar = %8, ProfileName = %9  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|İş akışı örnek kimliği|  
|Kayıt numarası|xs:long|Yayılan kaydın sıra numarası|  
|eventTime|xs:dateTime|Olay gösteriliyordu, UTC zamanı|  
|activityDefinitionId|xs:string|İş akışı içinde Kök etkinlik adı|  
|Durum|xs:string|İş akışının geçerli durumu.|  
|OriginalDefinitionIdentity|xs:string|Özgün iş akışı tanımı kimliği|  
|UpdatedDefinitionIdentity|xs:string|Güncelleştirilmiş iş akışı tanımı kimliği|  
|Ek Açıklamalar|xs:string|Bu olay için eklenen ek açıklamalar. Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</item > \< /öğeler >. Dize içeriyorsa hiçbir ek açıklama belirtilirse \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olayı bırakarak ek açıklamalar ve ek açıklama değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.|  
|profileName|xs:string|Adı veya yayılan bu olay ile sonuçlanan bir izleme profili|  
|WorkflowDefinitionIdentity|xs:string|İş akışı tanımı kimliği|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
