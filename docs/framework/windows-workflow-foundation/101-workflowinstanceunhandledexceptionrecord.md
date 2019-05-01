---
title: 101 - WorkflowInstanceUnhandledExceptionRecord
ms.date: 03/30/2017
ms.assetid: ab7d50a0-5347-4390-8445-1def4dfdff6a
ms.openlocfilehash: af7f471e135ed7ec782f7d9a5c7cee3de09e7187
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924611"
---
# <a name="101---workflowinstanceunhandledexceptionrecord"></a>101 - WorkflowInstanceUnhandledExceptionRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|101|  
|anahtar sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, bir iş akışı örneği WorkflowInstanceUnhandledExceptionRecord içerilip ETW İzleme katılımcı tarafından yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord WorkflowInstanceUnhandledExceptionRecord, InstanceId = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, özel durum = %9, ek açıklamalar = % 10, ProfileName = % 11  
  
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
|Ek Açıklamalar|xs:string|Bu olay için eklenen ek açıklamalar.  Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</item > \< /öğeler >.  Dize içeriyorsa hiçbir ek açıklama belirtilirse \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olayı bırakarak ek açıklamalar ve ek açıklama değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.|  
|profileName|xs:string|Adı veya yayılan bu olay ile sonuçlanan bir izleme profili|  
|HostReference|xs:string|Bu alan, barındırılan web hizmetleri için hizmet web hiyerarşideki benzersiz olarak tanımlar.  Onun biçimi olarak tanımlanmış olan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
