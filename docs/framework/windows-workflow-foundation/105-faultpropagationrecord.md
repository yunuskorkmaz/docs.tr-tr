---
title: 105 - FaultPropagationRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec9de51055812083430d9bcee780818187be04da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="105---faultpropagationrecord"></a>105 - FaultPropagationRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|105|  
|Anahtar Sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir etkinliği iş akışı örneği ile FaultPropagationRecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord FaultPropagationRecord, örnek kimliği = %1, kayıt numarası = %2, EventTime = = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = % 7 ' ye FaultHandlerActivityName = %8,  FaultHandlerActivityId %9, FaultHandlerActivityInstanceId = % 10, FaultHandlerActivityTypeName = % 11, hata = % 12, IsFaultSource = % 13, ek açıklamaları = % 14 ProfileName = = % 15  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|örnek kimliği|xs:GUID|İş akışı için örnek kimliği|  
|Kayıt numarası|xs:Long|Verilmiş kaydı sıra sayısı|  
|EventTime|xs: DateTime|Olay gösterilen zaman UTC zamanı|  
|FaultSourceActivityName|xs: String|Hataya gösterilen etkinlik adı|  
|FaultSourceActivityId|xs: String|Hataya gösterilen etkinlik kimliği|  
|FaultSourceActivityInstanceId|xs: String|Hataya gösterilen etkinlik örnek kimliği|  
|FaultSourceActivityTypeName|xs: String|Hataya gösterilen etkinlik türü|  
|FaultHandlerActivityName|xs: String|Hataya işleyici etkinliği görünen adı|  
|FaultHandlerActivityId|xs: String|Hataya işleyici etkinlik kimliği|  
|FaultHandlerActivityInstanceId|xs: String|Hataya işleyici etkinliği örnek kimliği|  
|FaultHandlerActivityTypeName|xs: String|Hataya işleyici etkinlik türü|  
|Hata|xs: String|Hata ayrıntıları|  
|IsFaultSource|xs:unsignedByte|Olay arıza kaynağından yayılan, gösterir|  
|Ek Açıklamalar|xs: String|Bu olay için eklenen ek açıklamalar.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.  Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.|  
|ProfileName|xs: String|Adı veya gösterilmesini bu olay sonuçlandı izleme profili|  
|HostReference|xs: String|Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
