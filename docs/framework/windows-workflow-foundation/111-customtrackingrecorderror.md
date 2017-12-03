---
title: 111 - CustomTrackingRecordError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d469fb12-e094-4d6c-9b4d-abd7ce0d17da
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5914837f8350c39fcf6f490eef44d77913af6f6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="111---customtrackingrecorderror"></a>111 - CustomTrackingRecordError
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|111|  
|Anahtar Sözcükler|Sorun giderme, ögesi, WFTracking UserEvents, EndToEndMonitoring,|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı örneği içinde bir etkinlik düzeyi hatasıyla CustomTrackingRecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord CustomTrackingRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ad = %4, ActivityName = %5, etkinlik kimliği = %6, ActivityInstanceId = % 7 ' ye ActivityTypeName = %8, veri = %9, ek açıklamaları = % 10, ProfileName = % 11  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|örnek kimliği|xs:GUID|İş akışı için örnek kimliği|  
|Kayıt numarası|xs:Long|Verilmiş kaydı sıra sayısı|  
|EventTime|xs: DateTime|Olay gösterilen zaman UTC zamanı|  
|Ad|xs: String|CustomTrackingRecord adı|  
|activityName|xs: String|CustomTrackingRecord gösterilen etkinlik adı|  
|Etkinlik Kimliği|xs: String|CustomTrackingRecord gösterilen etkinlik kimliği|  
|ActivityInstanceId|xs: String|CustomTrackingRecord gösterilen etkinlik örnek kimliği|  
|ActivityTypeName|xs: String|CustomTrackingRecord gösterilen etkinlik adı|  
|Veri|xs: String|Bu olay ile izlenen verileri.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "dataName" type="System.String =" > dataValue\</Madde > \< /öğelerini >.  Hiçbir veri izlenen sonra dizesini içeren \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve veri değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.  Aşağıdaki türlerden ToString() tarafından döndürülen değer depolanır; String,char,bool,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.Guid,System.DateTimeOffset,System.DateTime.  Diğer tüm türleri System.Runtime.Serialization.NetDataContractSerializer kullanarak serileştirilir.|  
|Ek Açıklamalar|xs: String|Bu olay için eklenen ek açıklamalar.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.  Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.|  
|ProfileName|xs: String|Adı veya gösterilmesini bu olay sonuçlandı izleme profili|  
|HostReference|xs: String|Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
