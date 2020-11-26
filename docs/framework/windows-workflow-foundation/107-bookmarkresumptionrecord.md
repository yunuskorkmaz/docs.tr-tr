---
title: 107 -- BookmarkResumptionRecord
ms.date: 03/30/2017
ms.assetid: aa2d37ed-2bfa-439b-89e8-a9354027f155
ms.openlocfilehash: 14557ef2726a60bcde49d30f9d6168fd831e613c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238866"
---
# <a name="107----bookmarkresumptionrecord"></a>107 -- BookmarkResumptionRecord

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|107|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, bir iş akışı örneği bir BookmarkResumptionRecord yaydığı zaman ETW izleme katılımcısı tarafından yayınlanır.  
  
## <a name="message"></a>İleti  

 TrackRecord = BookmarkResumptionRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ad = %4, SubInstanceID = %5, OwnerActivityName = %6, OwnerActivityId = %7, OwnerActivityInstanceId = %8, OwnerActivityTypeName = %9, ek açıklama = %10, ProfileName = %11  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|Adı|xs: String|Devam eden yer işaretinin adı|  
|SubInstanceID|xs: GUID|Yer işareti kapsamının kimliği|  
|OwnerActivityName|xs: String|Yer işareti etkinliğinin adı|  
|OwnerActivityId|xs: String|Yer işareti etkinliğinin kimliği|  
|OwnerActivityInstanceId|xs: String|Yer işareti etkinliğinin örnek kimliği|  
|OwnerActivityTypeName|xs: String|Yer işareti etkinliğinin türü|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örneği: ' Default Web site/Hesaplatokıpplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice ' olarak tanımlanmıştır|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
