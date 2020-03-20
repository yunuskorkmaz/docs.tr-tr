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
ms.openlocfilehash: b01f030c474e426cb87fb907f99f241eeb76a7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174764"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
`dateTimeInvalidLocalFormat` Evrensel Eşgüdümlü Zaman <xref:System.DateTime> (UTC) olarak depolanan bir örnek yalnızca yerel <xref:System.DateTime> örnekler için kullanılmak üzere tasarlanmış bir biçim kullanılarak biçimlendirildiğinde MDA etkinleştirilir. Bu MDA belirtilmeyen veya varsayılan <xref:System.DateTime> durumlar için etkinleştirilmez.  
  
## <a name="symptom"></a>Belirti  
 Uygulama, yerel bir biçim kullanarak <xref:System.DateTime> bir UTC örneğini el ile serihale getirerek:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Nedeni  
 Yöntemin <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 'z' biçimi, Sydney saati için "+10:00" gibi yerel saat dilimi mahsuplarını içerir. Bu nedenle, yalnızca değeri yerel <xref:System.DateTime> ise anlamlı bir sonuç üretecektir. Değer UTC saatiyse, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yerel saat dilimi mahsupını içerir, ancak saat dilimi belirticisini görüntülemez veya ayarlamaz.  
  
### <a name="resolution"></a>Çözüm  
 UTC <xref:System.DateTime> örnekleri UTC olduklarını gösteren bir şekilde biçimlendirilmelidir. UTC süresini belirtmek için UTC zamanları için önerilen biçim :  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Örneğin yerel, UTC veya belirtilmemiş <xref:System.DateTime> olup olmadığına <xref:System.DateTime.Kind%2A> bakılmaksızın, özelliğin kullanımını seri hale getiren bir "o" biçimi de vardır:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 Bu MDA çalışma süresini etkilemez.  
  
## <a name="output"></a>Çıktı  
 Bu MDA etkinleştirme sonucu özel bir çıkış yoktur., Ancak, çağrı yığını MDA etkinleştirilmiş <xref:System.DateTime.ToString%2A> arama konumunu belirlemek için kullanılabilir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Utc <xref:System.DateTime> değerini dolaylı olarak serileştiren bir uygulamayı <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> aşağıdaki şekilde veya sınıfı kullanarak düşünün.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 Ve <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> serileştirmeler varsayılan olarak serileştirme için yerel biçimleri kullanır. UTC gibi diğer değer türlerini <xref:System.DateTime> seri hale getirmek için ek seçenekler gereklidir.  
  
 Bu özel örnek `XmlDateTimeSerializationMode.RoundtripKind` için, `ToString` arama `XmlConvert`yı geçin. Bu, verileri UTC zamanı olarak serihale eder.  
  
 Bir <xref:System.Data.DataSet>kullanıyorsanız, <xref:System.Data.DataColumn.DateTimeMode%2A> nesne üzerindeki <xref:System.Data.DataColumn> özelliği <xref:System.Data.DataSetDateTime.Utc>.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.DateTimeFormatInfo>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
