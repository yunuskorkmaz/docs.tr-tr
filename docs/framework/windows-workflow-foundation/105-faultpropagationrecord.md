---
description: 'Hakkında daha fazla bilgi edinin: 105-FaultPropagationRecord'
title: 105 - FaultPropagationRecord
ms.date: 03/30/2017
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
ms.openlocfilehash: 95f82763606bf16219fa4234b5f6e7101c0954fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667687"
---
# <a name="105---faultpropagationrecord"></a>105 - FaultPropagationRecord

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|105|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, iş akışı örneğiyle bir etkinlik, FaultPropagationRecord yayar olduğunda ETW izleme katılımcısı tarafından yayılır.  
  
## <a name="message"></a>İleti  

 TrackRecord = FaultPropagationRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = %7, FaultHandlerActivityName = %8, FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId = %10, FaultHandlerActivityTypeName = %11, hata = %12, IsFaultSource = %13, ek açıklamalar = %14, ProfileName = %15  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|FaultSourceActivityName|xs: String|Hatayı oluşturan etkinliğin adı|  
|FaultSourceActivityId|xs: String|Hatayı oluşturan etkinliğin kimliği|  
|FaultSourceActivityInstanceId|xs: String|Hatayı oluşturan etkinliğin örnek kimliği|  
|FaultSourceActivityTypeName|xs: String|Hatayı oluşturan etkinliğin türü|  
|FaultHandlerActivityName|xs: String|Hata işleyicisi etkinliğinin görünen adı|  
|FaultHandlerActivityId|xs: String|Hata işleyicisi etkinliğinin kimliği|  
|FaultHandlerActivityInstanceId|xs: String|Hata işleyicisi etkinliğinin örnek kimliği|  
|FaultHandlerActivityTypeName|xs: String|Hata işleyicisi etkinliğinin türü|  
|Dayanıklı|xs: String|Hata ayrıntıları|  
|IsFaultSource|xs: unsignedByte|Olayın hata kaynağından yayıldığını belirtir|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örneği: ' Default Web site/Hesaplatokıpplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice ' olarak tanımlanmıştır|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
