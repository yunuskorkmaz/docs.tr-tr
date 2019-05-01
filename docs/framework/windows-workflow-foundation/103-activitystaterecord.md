---
title: 103 - ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 38cec570cffebf6af6d35df481cbec8c7dca8cd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924390"
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|103|  
|anahtar sözcükler|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, bir etkinlik iş akışı örneği içinde ActivityStateRecord içerilip ETW İzleme katılımcı tarafından yayıldığını  
  
## <a name="message"></a>İleti  
 TrackRecord ActivityStateRecord, InstanceId = = %1, RecordNumber = %2, EventTime = %3, durum = %4, ad = %5, etkinlik kimliği = %6, ActivityInstanceId = %7, ActivityTypeName = %8, bağımsız değişkenleri = %9, değişkenleri = % 10, ek açıklamalar = % 11, ProfileName = % 12  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|İş akışı örnek kimliği|  
|Kayıt numarası|xs:long|Yayılan kaydın sıra numarası|  
|eventTime|xs:dateTime|Olay gösteriliyordu, UTC zamanı|  
|Durum|xs:string|Etkinlik durumu|  
|Ad|xs:string|Olay yayılan etkinliğin görünen adı|  
|Etkinlik Kimliği|xs:string|Etkinlik Kimliği yayma etkinliği|  
|ActivityInstanceId|xs:string|Yayan etkinliğin etkinlik örneği kimliği|  
|ActivityTypeName|xs:string|Yayan etkinlik türü adı|  
|Arguments|xs:string|Bu olay ile izlenmekte olan bağımsız değişkenler.  Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "argumentName" type="System.String =" > argumentValue\</item > \< /öğeler >.  Bağımsız değişken olmadan izlenen sonra dizesini içeren \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olayı bırakarak ek açıklamalar ve ek açıklama değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.  Aşağıdaki türleri ToString() tarafından döndürülen şekilde, değer olarak depolanır; String,char,bool,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.Guid,System.DateTimeOffset,System.DateTime.  Diğer tüm türlerin System.Runtime.Serialization.NetDataContractSerializer kullanarak serileştirilir.|  
|Değişkenler|xs:string|Bu olay ile izlenen değişkenleri.  Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "variableName" type="System.String =" > variableValue\</item > \< /öğeler >.  Değişken izlenen sonra dizesini içeren \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olay ek açıklamalar bırakarak ve değişkenleri değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.  Aşağıdaki türleri ToString() tarafından döndürülen şekilde, değer olarak depolanır; String,char,bool,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.Guid,System.DateTimeOffset,System.DateTime.  Diğer tüm türlerin System.Runtime.Serialization.NetDataContractSerializer kullanarak serileştirilir.|  
|Ek Açıklamalar|xs:string|Bu olay için eklenen ek açıklamalar.  Değerlerini bir xml öğesi biçiminde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</item > \< /öğeler >.  Dize içeriyorsa hiçbir ek açıklama belirtilirse \<öğeler / >. ETW olay boyutu ETW arabellek boyutu veya ETW olayı için en fazla yükü sınırlıdır. Olay boyutu ETW limitlerini sonra olayı bırakarak ek açıklamalar ve ek açıklama değeri ile değiştirerek kesilmiş \<öğeleri >...  \< /öğeler >.|  
|profileName|xs:string|Adı veya yayılan bu olay ile sonuçlanan bir izleme profili|  
|HostReference|xs:string|Bu alan, barındırılan web hizmetleri için hizmet web hiyerarşideki benzersiz olarak tanımlar.  Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
