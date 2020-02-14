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
ms.openlocfilehash: 2fdace8a9c7bcc090fd801be3bd717e4a2b34a87
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217544"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
Evrensel Eşgüdümlü saat (UTC) olarak depolanan bir <xref:System.DateTime> örneği, yalnızca yerel <xref:System.DateTime> örnekleri için kullanılmak üzere tasarlanan bir biçim kullanılarak biçimlendirildiğinde `dateTimeInvalidLocalFormat` MDA etkinleştirilir. Bu MDA, belirtilmeyen veya varsayılan <xref:System.DateTime> örnekleri için etkinleştirilmemiş.  
  
## <a name="symptom"></a>Belirti  
 Bir uygulama, bir UTC <xref:System.DateTime> örneğini yerel bir biçim kullanarak el ile serileştiriliyor:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Nedeni  
 <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yöntemi için ' z ' biçimi, örneğin "+ 10:00", Sidney saati için yerel saat dilimi sapmasını içerir. Bu nedenle, <xref:System.DateTime> değeri yerel ise yalnızca anlamlı bir sonuç üretir. Değer UTC zamanı ise, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yerel saat dilimi sapmasını içerir, ancak saat dilimi tanımlayıcısını görüntülemez veya ayarlamalamaz.  
  
### <a name="resolution"></a>Çözüm  
 UTC <xref:System.DateTime> örnekleri UTC olduğunu belirten bir şekilde biçimlendirilmelidir. UTC zamanının UTC zamanını belirtmek için ' Z ' kullanması için önerilen biçim:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Örneğin yerel, UTC veya belirtilmemiş olsa da doğru şekilde seri hale getirilen <xref:System.DateTime.Kind%2A> özelliğini kullanan bir <xref:System.DateTime> seri hale getiren bir "o" biçimi de vardır:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, çalışma zamanını etkilemez.  
  
## <a name="output"></a>Çıktı  
 Bu MDA ' ın etkinleştirilmesiyle ilgili özel bir çıktı yoktur. ancak, çağrı yığını, MDA ' ı etkinleştiren <xref:System.DateTime.ToString%2A> çağrısının konumunu belirlemede kullanılabilir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Bir UTC <xref:System.DateTime> değerini, aşağıdaki şekilde <xref:System.Xml.XmlConvert> veya <xref:System.Data.DataSet> sınıfını kullanarak dolaylı olarak serileştirerek bir uygulamayı düşünün.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> ve <xref:System.Data.DataSet> serileştirmeler, varsayılan olarak serileştirme için yerel biçimler kullanır. UTC gibi diğer <xref:System.DateTime> değer türlerini seri hale getirmek için ek seçenekler gereklidir.  
  
 Bu belirli örnekte, `XmlConvert``ToString` çağrısına `XmlDateTimeSerializationMode.RoundtripKind` geçirin. Bu, verileri UTC saati olarak serileştirir.  
  
 <xref:System.Data.DataSet>kullanıyorsanız, <xref:System.Data.DataColumn> nesnesindeki <xref:System.Data.DataColumn.DateTimeMode%2A> özelliğini <xref:System.Data.DataSetDateTime.Utc>olarak ayarlayın.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.DateTimeFormatInfo>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
