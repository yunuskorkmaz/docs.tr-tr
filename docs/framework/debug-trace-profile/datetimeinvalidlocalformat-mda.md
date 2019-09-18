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
ms.openlocfilehash: 32217b9e681179c246560ff5b51b65b4f4e044d5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052880"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
Evrensel Eşgüdümlü saat (UTC) <xref:System.DateTime> olarak depolanan bir örnek, yalnızca yerel <xref:System.DateTime> örnekler için kullanılmak üzere tasarlanan bir biçim kullanılarak biçimlendirilirken MDAetkinleştirilir.`dateTimeInvalidLocalFormat` Bu mda belirtilmemiş veya varsayılan <xref:System.DateTime> örnekler için etkinleştirilmemiş.  
  
## <a name="symptom"></a>Belirti  
 Bir uygulama, bir UTC <xref:System.DateTime> örneğini yerel biçim kullanarak el ile serileştiriliyor:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Sebep  
 <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> Yöntemin ' z ' biçimi yerel saat dilimi sapmasını içerir, örneğin, Sidney saati için "+ 10:00". Bu nedenle, yalnızca değerinin <xref:System.DateTime> yerel olması durumunda anlamlı bir sonuç üretir. Değer UTC zamanı <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> ise, yerel saat dilimi sapmasını içerir, ancak saat dilimi tanımlayıcısını görüntülemez veya ayarlamalamaz.  
  
### <a name="resolution"></a>Çözüm  
 UTC <xref:System.DateTime> örneklerinin UTC olduğunu belirten bir şekilde biçimlendirilmesi gerekir. UTC zamanının UTC zamanını belirtmek için ' Z ' kullanması için önerilen biçim:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Örneğin yerel, UTC veya belirtilmemiş olsa da doğru şekilde seri hale <xref:System.DateTime> getirilen <xref:System.DateTime.Kind%2A> özelliği kullanan bir "o" biçimi de vardır:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, çalışma zamanını etkilemez.  
  
## <a name="output"></a>Çıkış  
 Bu mda ' ın etkinleştirilmesiyle ilgili özel bir çıktı yoktur. ancak, çağrı yığını, MDA ' ı etkinleştiren <xref:System.DateTime.ToString%2A> çağrının konumunu belirlemede kullanılabilir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki şekilde, <xref:System.DateTime> <xref:System.Xml.XmlConvert> veya <xref:System.Data.DataSet> sınıfını kullanarak UTC değerini dolaylı olarak serileştirtiren bir uygulamayı düşünün.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> Ve<xref:System.Data.DataSet> serileştirmeler varsayılan olarak serileştirme için yerel biçimler kullanır. UTC gibi diğer <xref:System.DateTime> değer türlerini seri hale getirmek için ek seçenekler gereklidir.  
  
 Bu belirli örnek için, `XmlDateTimeSerializationMode.RoundtripKind` `ToString` çağrısına `XmlConvert`geçin. Bu, verileri UTC saati olarak serileştirir.  
  
 Kullanıyorsanız <xref:System.Data.DataSet> <xref:System.Data.DataColumn.DateTimeMode%2A> , nesnesi<xref:System.Data.DataColumn> üzerinde özelliğini olarak<xref:System.Data.DataSetDateTime.Utc>ayarlayın.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.DateTimeFormatInfo>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
