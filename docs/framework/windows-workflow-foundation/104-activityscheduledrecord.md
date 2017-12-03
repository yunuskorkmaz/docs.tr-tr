---
title: 104 - ActivityScheduledRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae202178-8fb1-4646-a3aa-18beeda8ff93
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36196f6814081a059e4a04de0ee9f0dd42d79bbe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="104---activityscheduledrecord"></a>104 - ActivityScheduledRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|104|  
|Anahtar Sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı örneği içinde bir etkinlik ActivityScheduledRecord yayar, bu olay ETW İzleme katılımcı tarafından gösterilen  
  
## <a name="message"></a>İleti  
 TrackRecord ActivityScheduledRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ad = %4, etkinlik kimliği = %5, ActivityInstanceId = %6, ActivityTypeName = % 7 ' ye ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName % 11, ek açıklamaları = % 12, ProfileName = % 13 =  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|örnek kimliği|xs:GUID|İş akışı için örnek kimliği|  
|Kayıt numarası|xs:Long|Verilmiş kaydı sıra sayısı|  
|EventTime|xs: DateTime|Olay gösterilen zaman UTC zamanı|  
|Ad|xs: String|Alt aktivitesi etkinlik adı|  
|Etkinlik Kimliği|xs: String|Zamanlanmış alt etkinliğin etkinlik kimliği|  
|ActivityInstanceId|xs: String|Alt aktivitesi etkinlik örnek kimliği|  
|ActivityTypeName|xs: String|İptal işlemi istenen etkinlik türü|  
|ChildActivityName|xs: String|Zamanlanan etkinlik adı|  
|ChildActivityId|xs: String|Zamanlanan etkinlik kimliği|  
|ChildActivityInstanceId|xs: String|Zamanlanan etkinlikten örnek kimliği|  
|ChildActivityTypeName|xs: String|Zamanlanan etkinlik türü|  
|Ek Açıklamalar|xs: String|Bu olay için eklenen ek açıklamalar.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.  Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.|  
|ProfileName|xs: String|Adı veya gösterilmesini bu olay sonuçlandı izleme profili|  
|HostReference|xs: String|Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
