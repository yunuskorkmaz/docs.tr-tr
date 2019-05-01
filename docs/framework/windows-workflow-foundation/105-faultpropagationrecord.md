---
title: 105 - FaultPropagationRecord
ms.date: 03/30/2017
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
ms.openlocfilehash: c48f42a91ad9a15b49aad8c1ab684f2348954174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924208"
---
# <a name="105---faultpropagationrecord"></a>105 - FaultPropagationRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|105|  
|anahtar sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay bir etkinliği iş akışı örneği ile FaultPropagationRecord içerilip ETW İzleme katılımcı tarafından yayılır.  
  
## <a name="message"></a>İleti  
 TrackRecord FaultPropagationRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = %7, FaultHandlerActivityName = %8  FaultHandlerActivityId %9, FaultHandlerActivityInstanceId = % 10, FaultHandlerActivityTypeName = % 11, hata = % 12, IsFaultSource = % 13, ek açıklamalar = % 14, ProfileName = = % 15  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|İş akışı örnek kimliği|  
|Kayıt numarası|xs:long|Yayılan kaydın sıra numarası|  
|eventTime|xs:dateTime|Olay gösteriliyordu, UTC zamanı|  
|FaultSourceActivityName|xs:string|Hata yayılan etkinlik adı|  
|FaultSourceActivityId|xs:string|Hata yayılan etkinliğin kimliği|  
|FaultSourceActivityInstanceId|xs:string|Hata yayılan etkinliğin örnek kimliği|  
|FaultSourceActivityTypeName|xs:string|Hata yayılan etkinlik türü|  
|faultHandlerActivityName|xs:string|Hata işleyicisi etkinliğin görünen adı|  
|FaultHandlerActivityId|xs:string|Hata işleyicisi etkinliğin kimliği|  
|FaultHandlerActivityInstanceId|xs:string|Hata işleyicisi etkinliğin örnek kimliği|  
|FaultHandlerActivityTypeName|xs:string|Hata işleyicisi etkinliğin türü|  
|Hata|xs:string|Hata ayrıntıları|  
|IsFaultSource|xs:unsignedByte|Olay bir hataya kaynaktan gösteriliyordu gösterir|  
|Ek Açıklamalar|xs:string|Bu olay için eklenen ek açıklamalar.  Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</item > \< /öğeler >.  Dize içeriyorsa hiçbir ek açıklama belirtilirse \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olayı bırakarak ek açıklamalar ve ek açıklama değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.|  
|profileName|xs:string|Adı veya yayılan bu olay ile sonuçlanan bir izleme profili|  
|HostReference|xs:string|Bu alan, barındırılan web hizmetleri için hizmet web hiyerarşideki benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
