---
title: 101 - WorkflowInstanceUnhandledExceptionRecord
ms.date: 03/30/2017
ms.assetid: ab7d50a0-5347-4390-8445-1def4dfdff6a
ms.openlocfilehash: af7f471e135ed7ec782f7d9a5c7cee3de09e7187
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512746"
---
# <a name="101---workflowinstanceunhandledexceptionrecord"></a>101 - WorkflowInstanceUnhandledExceptionRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|101|  
|Anahtar Sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı örneği WorkflowInstanceUnhandledExceptionRecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord WorkflowInstanceUnhandledExceptionRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = % 7 ' ye SourceTypeName = %8, özel durum = %9, ek açıklamaları = % 10, ProfileName = % 11  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|örnek kimliği|xs:GUID|İş akışı için örnek kimliği|  
|Kayıt numarası|xs:Long|Verilmiş kaydı sıra sayısı|  
|EventTime|xs: DateTime|Olay gösterilen zaman UTC zamanı|  
|ActivityDefinitionId|xs: String|İş akışı Kök etkinlik adı|  
|SourceName|xs: String|UnhandledException kaynaklanan hatalı kaynak etkinlik adı|  
|SourceId|xs: String|Hataya kaynak etkinliğin etkinlik kimliği|  
|SourceInstanceId|xs: String|Hataya kaynak etkinliği etkinlik örnek kimliği|  
|SourceTypeName|xs: String|UnhandledException kaynaklanan hatalı kaynak etkinlik türü adı|  
|Özel Durum|xs: String|İşlenmeyen özel durum için özel durum ayrıntıları|  
|Ek Açıklamalar|xs: String|Bu olay için eklenen ek açıklamalar.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.  Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.|  
|ProfileName|xs: String|Adı veya gösterilmesini bu olay sonuçlandı izleme profili|  
|HostReference|xs: String|Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.  Buna ait biçimi olarak tanımlanır ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
