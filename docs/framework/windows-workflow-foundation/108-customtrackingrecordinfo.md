---
title: 108 - CustomTrackingRecordInfo
ms.date: 03/30/2017
ms.assetid: 5bee501e-4e00-42cd-b949-e88009c3d4e8
ms.openlocfilehash: 5fe45d62446d4dee23d29bed03dd490d8cb8efb8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238853"
---
# <a name="108---customtrackingrecordinfo"></a>108 - CustomTrackingRecordInfo

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|108|  
|Anahtar sözcükler|Kullanıcıetkinlikleri, EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, bir iş akışı örneği içindeki bir etkinlik düzey bilgiyle CustomTrackingRecord ' i yayıyorsa ETW izleme katılımcısı tarafından yayılır.  
  
## <a name="message"></a>İleti  

 TrackRecord = CustomTrackingRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ad = %4, ActivityName = %5, ActivityID = %6, ActivityInstanceId = %7, ActivityTypeName = %8, veri = %9, ek açıklamalar = %10, ProfileName = %11  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|Adı|xs: String|CustomTrackingRecord adı|  
|Özelliğinde|xs: String|CustomTrackingRecord ' a yayılan etkinliğin adı|  
|Etkinlik kimliği|xs: String|CustomTrackingRecord öğesini oluşturan etkinliğin kimliği|  
|ActivityInstanceId|xs: String|CustomTrackingRecord öğesini oluşturan etkinliğin örnek kimliği|  
|ActivityTypeName|xs: String|CustomTrackingRecord ' a yayılan etkinliğin adı|  
|Veriler|xs: String|Bu olayla izlenen veriler.  Değerler, dataValue biçimindeki bir XML öğesinde depolanır \<items> \< item  name = "dataName" type="System.String"> \</item> \</items> .  Hiçbir veri izlenmediyse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve veri değeri \<items> .. \</items> . ile değiştirilerek olay kesilir.  Aşağıdaki türler, ToString () tarafından döndürülen değerleri olarak depolanır. dize, Char, bool, int, Short, Long, uint, ushort, ulong, System. Single, float, Double, System. Guid, System. DateTimeOffset, System. DateTime.  Tüm diğer türler System. Runtime. Serialization. NetDataContractSerializer kullanılarak serileştirilir.|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı ' örneği: ' Default Web site/Hesaplatokıpplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice ' olarak tanımlanmıştır|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
