---
title: 107--BookmarkResumptionRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa2d37ed-2bfa-439b-89e8-a9354027f155
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 247a439dcbe566e74fd0157fbd92b9cb6c96e375
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="107----bookmarkresumptionrecord"></a>107--BookmarkResumptionRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|107|  
|Anahtar Sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı örneği bir BookmarkResumptionRecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord BookmarkResumptionRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ad = %4, SubInstanceID = %5, OwnerActivityName = %6, OwnerActivityId = % 7 ' ye OwnerActivityInstanceId = %8, OwnerActivityTypeName = %9, ek açıklamaları = % 10, ProfileName = % 11  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|örnek kimliği|xs:GUID|İş akışı için örnek kimliği|  
|Kayıt numarası|xs:Long|Verilmiş kaydı sıra sayısı|  
|EventTime|xs: DateTime|Olay gösterilen zaman UTC zamanı|  
|Ad|xs: String|Devam ettirildi işaretinin adı|  
|SubInstanceID|xs:GUID|Yer işareti kapsam kimliği|  
|OwnerActivityName|xs: String|Yer işareti etkinlik adı|  
|OwnerActivityId|xs: String|Yer işareti etkinlik kimliği|  
|OwnerActivityInstanceId|xs: String|Yer işareti etkinlik örnek kimliği|  
|OwnerActivityTypeName|xs: String|Yer işareti etkinlik türü|  
|Ek Açıklamalar|xs: String|Bu olay için eklenen ek açıklamalar.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.  Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.|  
|ProfileName|xs: String|Adı veya gösterilmesini bu olay sonuçlandı izleme profili|  
|HostReference|xs: String|Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
