---
title: 112 - WorkflowInstanceSuspendedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc825c7c-8c90-48f7-9336-9a978a8246c6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d1b62d4c55f216ccb09d14515800fccd29fe974
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="112---workflowinstancesuspendedrecord"></a>112 - WorkflowInstanceSuspendedRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|112|  
|Anahtar Sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı örneği WorkflowInstanceSuspended kaydı yayar, bu olay tarafından ETW İzleme katılımcı yayınlanır.  
  
## <a name="message"></a>İleti  
 TrackRecord WorkflowInstanceSuspendedRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamaları = %6, ProfileName = %7  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|örnek kimliği|xs:GUID|İş akışı için örnek kimliği|  
|Kayıt numarası|xs:Long|Verilmiş kaydı sıra sayısı|  
|EventTime|xs: DateTime|Olay gösterilen zaman UTC zamanı|  
|ActivityDefinitionId|xs: String|İş akışı Kök etkinlik adı|  
|Neden|xs: String|İş akışı nedenle askıya alındı|  
|Ek Açıklamalar|xs: String|Bu olay için eklenen ek açıklamalar.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.  Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.|  
|ProfileName|xs: String|Adı veya gösterilmesini bu olay sonuçlandı izleme profili|  
|HostReference|xs: String|Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
