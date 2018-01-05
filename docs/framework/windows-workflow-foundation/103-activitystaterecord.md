---
title: 103 - ActivityStateRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62916de4d5077b8031ee353ca49a7d51a51ffd8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|103|  
|Anahtar Sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir iş akışı örneği içinde bir etkinlik ActivityStateRecord yayar, bu olay ETW İzleme katılımcı tarafından gösterilen  
  
## <a name="message"></a>İleti  
 TrackRecord ActivityStateRecord, örnek kimliği = = %1, kayıt numarası = %2, EventTime = %3, durum = %4, ad = %5, etkinlik kimliği = %6, ActivityInstanceId = % 7 ' ye ActivityTypeName = %8, bağımsız değişkenler = %9, değişkenleri = % 10, ek açıklamaları = % 11, ProfileName = % 12  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|örnek kimliği|xs:GUID|İş akışı için örnek kimliği|  
|Kayıt numarası|xs:Long|Verilmiş kaydı sıra sayısı|  
|EventTime|xs: DateTime|Olay gösterilen zaman UTC zamanı|  
|Durum|xs: String|Etkinlik durumu|  
|Ad|xs: String|Olay gösterilen etkinlik görünen adı|  
|Etkinlik Kimliği|xs: String|Verme etkinliğin etkinlik kimliği|  
|ActivityInstanceId|xs: String|Verme etkinliğin etkinlik örnek kimliği|  
|ActivityTypeName|xs: String|Verme etkinlik türü adı|  
|Arguments|xs: String|Bu olayla izlenmekte olan bağımsız değişkenler.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "argumentName" type="System.String =" > argumentValue\</Madde > \< /öğelerini >.  Bağımsız değişkenler izlenmekte olan sonra dizesini içeren \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.  Aşağıdaki türlerden ToString() tarafından döndürülen değer depolanır; String,char,bool,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.Guid,System.DateTimeOffset,System.DateTime.  Diğer tüm türleri System.Runtime.Serialization.NetDataContractSerializer kullanarak serileştirilir.|  
|Değişkenler|xs: String|Bu olayla izlenmekte olan değişkenler.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "variableName" type="System.String =" > variableValue\</Madde > \< /öğelerini >.  Değişken izlenmekte olan sonra dizesini içeren \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay tarafından ek açıklamalar bırakarak ve değişkenleri değeriyle değiştirme kesilir \<öğeleri >...  \< /öğelerini >.  Aşağıdaki türlerden ToString() tarafından döndürülen değer depolanır; String,char,bool,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.Guid,System.DateTimeOffset,System.DateTime.  Diğer tüm türleri System.Runtime.Serialization.NetDataContractSerializer kullanarak serileştirilir.|  
|Ek Açıklamalar|xs: String|Bu olay için eklenen ek açıklamalar.  Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.  Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >. ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.|  
|ProfileName|xs: String|Adı veya gösterilmesini bu olay sonuçlandı izleme profili|  
|HostReference|xs: String|Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
