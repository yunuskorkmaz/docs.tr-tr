---
title: dateTimeInvalidLocalFormat MDA
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 380334dbe9b91ea369de6cbe58686a9a74254c2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148232"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
`dateTimeInvalidLocalFormat` MDA etkinleştirilmiş olduğunda bir <xref:System.DateTime> yalnızca yerel için kullanılmak üzere tasarlanan bir biçimi kullanılarak biçimlendirilmiş bir Eşgüdümlü Evrensel Saat (UTC) olarak depolanan örneği <xref:System.DateTime> örnekleri. Bu mda'nın belirtilmemiş veya varsayılan etkinleştirilmedi <xref:System.DateTime> örnekleri.  
  
## <a name="symptom"></a>Belirti  
 Bir uygulamayı el ile bir UTC serileştiren <xref:System.DateTime> yerel biçimini kullanarak örneği:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Sebep  
 'z' biçimlendirmek için <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yöntemi içeren yerel saat dilimi uzaklığı, örneğin, "+ 10:00" Sidney kez. Bu nedenle, bunu yalnızca anlamlı bir sonuç ise üretecektir değerini <xref:System.DateTime> yereldir. UTC saat değeriyse <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yerel saatini içeren dilimi uzaklığı, ancak bunu dotnetclıtools'u görüntülemiyor ve saat dilimi belirteci ayarlayın.  
  
### <a name="resolution"></a>Çözüm  
 UTC <xref:System.DateTime> örnekleri UTC olduklarını bildiren bir şekilde biçimlendirilmelidir. UTC saatleri UTC saati belirtmek için 'Z' kullanmak için önerilen biçim:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Ayrıca serileştiren bir "o" biçim vardır bir <xref:System.DateTime> ipconfigurations <xref:System.DateTime.Kind%2A> örneği yerel olup olmadığına bakılmaksızın doğru olarak serileştiren özelliğini, UTC veya belirtilmeyen:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu MDA, çalışma zamanı etkilemez.  
  
## <a name="output"></a>Çıkış  
 Bu MDA etkinleştirme sonucu olarak özel çıkış yok., Bununla birlikte, çağrı yığını konumunu belirlemek için kullanılabilir <xref:System.DateTime.ToString%2A> MDA etkinleştirilmiş çağrısı.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 UTC biçiminde dolaylı olarak serileştiren bir uygulama düşünün <xref:System.DateTime> kullanarak değer <xref:System.Xml.XmlConvert> veya <xref:System.Data.DataSet> sınıfında aşağıdaki şekilde yapılandırılır.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> Ve <xref:System.Data.DataSet> serializations varsayılan olarak seri hale getirme için yerel biçimleri kullanın. Ek seçenekler, diğer türleri serileştirmek için gereklidir, <xref:System.DateTime> UTC gibi değerler.  
  
 Bu örnek için geçirin `XmlDateTimeSerializationMode.RoundtripKind` için `ToString` çağırmak `XmlConvert`. Bu veriler UTC saati olarak serileştirir.  
  
 Kullanılıyorsa bir <xref:System.Data.DataSet>ayarlayın <xref:System.Data.DataColumn.DateTimeMode%2A> özelliği <xref:System.Data.DataColumn> nesnesini <xref:System.Data.DataSetDateTime.Utc>.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.DateTimeFormatInfo>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
