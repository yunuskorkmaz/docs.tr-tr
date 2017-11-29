---
title: 106 - CancelRequestRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36de6eabb247cb59e8759032e5cd6d6996b52d45
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="106---cancelrequestrecord"></a>106 - CancelRequestRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|106|  
|Anahtar Sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı örneği içinde bir etkinlik cancelrequestedrecord yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord CancelRequestedRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ad = %4, etkinlik kimliği = %5, ActivityInstanceId = %6, ActivityTypeName = % 7 ' ye ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName % 11, ek açıklamaları = % 12, ProfileName = % 13 =  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|örnek kimliği|xs:GUID|İş akışı için örnek kimliği|  
|Kayıt numarası|xs:Long|Verilmiş kaydı sıra sayısı|  
|EventTime|xs: DateTime|Olay gösterilen zaman UTC zamanı|  
|Ad|xs: String|İptal işlemi istenen etkinlik adı|  
|Etkinlik Kimliği|xs: String|İptal işlemi istenen etkinlik kimliği|  
|ActivityInstanceId|xs: String|İptal işlemi istenen etkinlik örnek kimliği|  
|ActivityTypeName|xs: String|İptal işlemi istenen etkinlik türü|  
|ChildActivityName|xs: String|İptal ediliyor etkinlik adı|  
|ChildActivityId|xs: String|İptal ediliyor etkinlik kimliği|  
|ChildActivityInstanceId|xs: String|İptal ediliyor etkinlik örnek kimliği|  
|ChildActivityTypeName|xs: String|İptal ediliyor etkinlik türü|  
|Ek Açıklamalar|xs: String|Bu olay için eklenen ek açıklamalar.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.  Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.|  
|ProfileName|xs: String|Adı veya gösterilmesini bu olay sonuçlandı izleme profili|  
|HostReference|xs: String|Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
