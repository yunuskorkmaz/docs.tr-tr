---
title: dateTimeInvalidLocalFormat MDA
description: UTC saklı bir tarih saat değeri yalnızca yerel bir tarih saat biçimi aldığında etkinleştirilen Datetimeınvalidlocalformat yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: d092b93af55d2cdf14e9284d8cffcdc8440cbf81
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415998"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
`dateTimeInvalidLocalFormat` <xref:System.DateTime> Evrensel Eşgüdümlü saat (UTC) olarak depolanan bir örnek, yalnızca yerel örnekler için kullanılmak üzere tasarlanan bir biçim kullanılarak biçimlendirilirken MDA etkinleştirilir <xref:System.DateTime> . Bu MDA belirtilmemiş veya varsayılan örnekler için etkinleştirilmemiş <xref:System.DateTime> .  
  
## <a name="symptom"></a>Belirti  
 Bir uygulama, bir UTC <xref:System.DateTime> örneğini yerel biçim kullanarak el ile serileştiriliyor:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Nedeni  
 Yöntemin ' z ' biçimi <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> Yerel Saat dilimi sapmasını içerir, örneğin, Sidney saati için "+ 10:00". Bu nedenle, yalnızca değerinin yerel olması durumunda anlamlı bir sonuç üretir <xref:System.DateTime> . Değer UTC zamanı ise, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> Yerel Saat dilimi sapmasını içerir, ancak saat dilimi tanımlayıcısını görüntülemez veya ayarlamalamaz.  
  
### <a name="resolution"></a>Çözüm  
 UTC <xref:System.DateTime> ÖRNEKLERININ UTC olduğunu belirten bir şekilde biçimlendirilmesi gerekir. UTC zamanının UTC zamanını belirtmek için ' Z ' kullanması için önerilen biçim:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <xref:System.DateTime> <xref:System.DateTime.Kind%2A> Örneğin yerel, UTC veya belirtilmemiş olsa da doğru şekilde seri hale getirilen özelliği kullanan bir "o" biçimi de vardır:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, çalışma zamanını etkilemez.  
  
## <a name="output"></a>Çıktı  
 Bu MDA ' ın etkinleştirilmesiyle ilgili özel bir çıktı yoktur. ancak, çağrı yığını, MDA ' ı etkinleştiren çağrının konumunu belirlemede kullanılabilir <xref:System.DateTime.ToString%2A> .  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 <xref:System.DateTime> <xref:System.Xml.XmlConvert> Aşağıdaki şekilde, veya SıNıFıNı kullanarak UTC değerini dolaylı olarak serileştirtiren bir uygulamayı düşünün <xref:System.Data.DataSet> .  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert>Ve <xref:System.Data.DataSet> serileştirmeler varsayılan olarak serileştirme için yerel biçimler kullanır. UTC gibi diğer değer türlerini seri hale getirmek için ek seçenekler gereklidir <xref:System.DateTime> .  
  
 Bu belirli örnek için, çağrısına geçin `XmlDateTimeSerializationMode.RoundtripKind` `ToString` `XmlConvert` . Bu, verileri UTC saati olarak serileştirir.  
  
 Kullanıyorsanız <xref:System.Data.DataSet> , <xref:System.Data.DataColumn.DateTimeMode%2A> nesnesi üzerinde özelliğini <xref:System.Data.DataColumn> olarak ayarlayın <xref:System.Data.DataSetDateTime.Utc> .  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.DateTimeFormatInfo>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
