---
title: 112 - WorkflowInstanceSuspendedRecord
ms.date: 03/30/2017
ms.assetid: bc825c7c-8c90-48f7-9336-9a978a8246c6
ms.openlocfilehash: 53ceec38973d2e964733736e6297007cdba66398
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924091"
---
# <a name="112---workflowinstancesuspendedrecord"></a>112 - WorkflowInstanceSuspendedRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|112|  
|anahtar sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, bir iş akışı örneği WorkflowInstanceSuspended kayıt içerilip ETW İzleme katılımcı tarafından yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord WorkflowInstanceSuspendedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamalar = %6, ProfileName %7 =  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|İş akışı örnek kimliği|  
|Kayıt numarası|xs:long|Yayılan kaydın sıra numarası|  
|eventTime|xs:dateTime|Olay gösteriliyordu, UTC zamanı|  
|activityDefinitionId|xs:string|İş akışı içinde Kök etkinlik adı|  
|Neden|xs:string|Neden iş akışını askıya alındı|  
|Ek Açıklamalar|xs:string|Bu olay için eklenen ek açıklamalar.  Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</item > \< /öğeler >.  Dize içeriyorsa hiçbir ek açıklama belirtilirse \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olayı bırakarak ek açıklamalar ve ek açıklama değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.|  
|profileName|xs:string|Adı veya yayılan bu olay ile sonuçlanan bir izleme profili|  
|HostReference|xs:string|Bu alan, barındırılan web hizmetleri için hizmet web hiyerarşideki benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
