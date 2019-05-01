---
title: 106 - CancelRequestRecord
ms.date: 03/30/2017
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
ms.openlocfilehash: 4d2e9bd271c04a9e26150e7dddffc33963dfe0a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924182"
---
# <a name="106---cancelrequestrecord"></a>106 - CancelRequestRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|106|  
|anahtar sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay iş akışı örneği içinde bir etkinlik cancelrequestedrecord içerilip ETW İzleme katılımcı tarafından yayılır.  
  
## <a name="message"></a>İleti  
 TrackRecord CancelRequestedRecord, InstanceId = = %1, RecordNumber = %2, EventTime = %3, ad = %4, etkinlik kimliği = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName % 11, ek açıklamalar = 12, % ProfileName = % 13 =  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|İş akışı örnek kimliği|  
|Kayıt numarası|xs:long|Yayılan kaydın sıra numarası|  
|eventTime|xs:dateTime|Olay gösteriliyordu, UTC zamanı|  
|Ad|xs:string|İptal işlemi istenen etkinlik adı|  
|Etkinlik Kimliği|xs:string|İptal işlemi istendi. etkinlik kimliği|  
|ActivityInstanceId|xs:string|İptal işlemi istenen etkinlik örneği kimliği|  
|ActivityTypeName|xs:string|İptal işlemi istenen etkinlik türü|  
|childActivityName|xs:string|İptal ediliyor etkinliğin adı|  
|ChildActivityId|xs:string|İptal ediliyor etkinliğin kimliği|  
|ChildActivityInstanceId|xs:string|Örnek kimliği etkinliği iptal ediliyor|  
|ChildActivityTypeName|xs:string|İptal ediliyor etkinlik türü|  
|Ek Açıklamalar|xs:string|Bu olay için eklenen ek açıklamalar.  Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</item > \< /öğeler >.  Dize içeriyorsa hiçbir ek açıklama belirtilirse \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olayı bırakarak ek açıklamalar ve ek açıklama değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.|  
|profileName|xs:string|Adı veya yayılan bu olay ile sonuçlanan bir izleme profili|  
|HostReference|xs:string|Bu alan, barındırılan web hizmetleri için hizmet web hiyerarşideki benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
