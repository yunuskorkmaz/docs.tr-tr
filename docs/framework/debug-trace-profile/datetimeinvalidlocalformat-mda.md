---
title: dateTimeInvalidLocalFormat MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c70315cec9dca23605dc46f4cf090f4358c76e53
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
`dateTimeInvalidLocalFormat` MDA etkinleştirilirse, bir <xref:System.DateTime> yalnızca yerel için kullanılması hedeflenen bir biçimi kullanarak bir Evrensel Eşgüdümlü saate (UTC) biçimli olarak depolanan örneği <xref:System.DateTime> örnekleri. Bu MDA belirtilmemiş veya varsayılan etkinleştirilmedi <xref:System.DateTime> örnekleri.  
  
## <a name="symptom"></a>Belirti  
 Bir uygulamayı el ile bir UTC serileştirme <xref:System.DateTime> yerel biçimini kullanarak örneği:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Sebep  
 'z' biçimlendirmek için <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yöntemi içeren yerel saat dilimi konumu, örneğin, "+ 10:00" Sidney süre. Bu nedenle, onu yalnızca anlamlı bir sonuç varsa üretecektir değerini <xref:System.DateTime> yereldir. UTC saat değeri geçerliyse <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yerel saati içeren bölge uzaklığı, ancak bırakmaz görüntülemek veya saat dilimi belirleyici ayarlayın.  
  
### <a name="resolution"></a>Çözüm  
 UTC <xref:System.DateTime> örnekleri UTC olduğunu gösterir şekilde biçimlendirilmelidir. UTC saatleri UTC saati belirtmek için 'Z' kullanmak Önerilen biçimi:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Ayrıca serileştiren bir "o" biçiminde olan bir <xref:System.DateTime> yapmayı kullanımını <xref:System.DateTime.Kind%2A> örneği yerel olup olmadığına bakılmaksızın doğru olarak serileştiren özelliği, UTC veya belirtilmemiş:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA çalışma etkilemez.  
  
## <a name="output"></a>Çıkış  
 Bu MDA etkinleştirme sonucunda özel çıkış yok., ancak, çağrı yığını konumunu belirlemek için kullanılabilir <xref:System.DateTime.ToString%2A> MDA etkinleştirilmiş çağrısı.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Bir UTC dolaylı olarak serileştiren bir uygulamayı göz önünde bulundurun <xref:System.DateTime> kullanarak değer <xref:System.Xml.XmlConvert> veya <xref:System.Data.DataSet> aşağıdaki şekilde sınıfı.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> Ve <xref:System.Data.DataSet> serializations seri hale getirme için yerel biçimler varsayılan olarak kullanın. Ek seçenekler diğer türleri serileştirmek için gereklidir, <xref:System.DateTime> UTC gibi değerler.  
  
 Bu belirli örneğin geçirin `XmlDateTimeSerializationMode.RoundtripKind` için `ToString` çağırmak `XmlConvert`. Bu veriler UTC saati olarak serileştirir.  
  
 Kullanılıyorsa bir <xref:System.Data.DataSet>ayarlayın <xref:System.Data.DataColumn.DateTimeMode%2A> özelliği <xref:System.Data.DataColumn> nesnesine <xref:System.Data.DataSetDateTime.Utc>.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
