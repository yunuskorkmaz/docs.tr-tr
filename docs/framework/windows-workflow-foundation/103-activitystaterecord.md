---
description: 'Hakkında daha fazla bilgi edinin: 103-ActivityStateRecord'
title: 103 - ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 14afbfdb0869b6ee65e1482fa73aa36ccd58f307
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668129"
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|103|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir iş akışı örneği içindeki bir etkinlik ActivityStateRecord yayar olduğunda ETW izleme katılımcısı tarafından yayılır  
  
## <a name="message"></a>İleti  

 TrackRecord = ActivityStateRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, durum = %4, ad = %5, ActivityID = %6, ActivityInstanceId = %7, ActivityTypeName = %8, arguments = %9, değişkenler = %10, ek açıklama = %11, ProfileName = %12  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|Durum|xs: String|Etkinliğin durumu|  
|Name|xs: String|Olayı oluşturan etkinliğin görünen adı|  
|ActivityId|xs: String|Yayma etkinliğinin etkinlik kimliği|  
|ActivityInstanceId|xs: String|Yayma etkinliğinin etkinlik örneği kimliği|  
|ActivityTypeName|xs: String|Yayma etkinliğinin tür adı|  
|Bağımsız değişkenler|xs: String|Bu olayla izlenen bağımsız değişkenler.  Değerler, bir XML öğesinde, \<items> \< item  name = "argumentName" type="System.String"> bağımsız değişkenler değerindeki bir XML öğesinde depolanır \</item> \</items> .  Hiçbir bağımsız değişken izlenmediyse, dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .  Aşağıdaki türler, ToString () tarafından döndürülen değerleri olarak depolanır. dize, Char, bool, int, Short, Long, uint, ushort, ulong, System. Single, float, Double, System. Guid, System. DateTimeOffset, System. DateTime.  Tüm diğer türler System. Runtime. Serialization. NetDataContractSerializer kullanılarak serileştirilir.|  
|Değişkenler|xs: String|Bu olayla izlenen değişkenler.  Değerler, VariableValue biçimindeki bir XML öğesinde depolanır \<items> \< item  name = "variableName" type="System.String"> \</item> \</items> .  Hiçbir değişken izlenmediyse, dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve değişkenler değeri \<items> .. \</items> . ile değiştirilerek olay kesilir.  Aşağıdaki türler, ToString () tarafından döndürülen değerleri olarak depolanır. dize, Char, bool, int, Short, Long, uint, ushort, ulong, System. Single, float, Double, System. Guid, System. DateTimeOffset, System. DateTime.  Tüm diğer türler System. Runtime. Serialization. NetDataContractSerializer kullanılarak serileştirilir.|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örneği: ' Default Web site/Hesaplatokıpplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice ' olarak tanımlanmıştır|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
