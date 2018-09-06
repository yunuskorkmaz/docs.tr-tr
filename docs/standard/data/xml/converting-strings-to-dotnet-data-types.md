---
title: .NET Framework veri türleri için dizeleri dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc07779f03784cd32524e1b1189faae343710a05
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865793"
---
# <a name="converting-strings-to-net-framework-data-types"></a>.NET Framework veri türleri için dizeleri dönüştürme
Bir dizeyi bir .NET Framework veri türüne dönüştürmek istiyorsanız kullanmanız **XmlConvert** uygulama gereksinimlerine en uygun yöntemi. Kullanılabilir tüm dönüştürme yöntemleri listesi **XmlConvert** sınıfı <xref:System.Xml.XmlConvert>.  
  
 Döndürülen dize **ToString** yöntemi geçirilen verileri dize sürümüdür. Ayrıca, kullanarak birden fazla .NET Framework türü vardır **XmlConvert** yöntemlere kullanmayın henüz sınıfı **System.Convert** sınıfı. **XmlConvert** sınıfı XML Şeması (XSD) veri türü belirtimi izler ve bir veri türü olan **XmlConvert** eşleyebilirsiniz.  
  
 Aşağıdaki tablo, .NET Framework veri türleri ve XML Şeması (XSD) veri türü eşlemesi kullanarak döndürülen dize türleri listelenmektedir. Bu .NET Framework türleri kullanılarak işlenemez **System.Convert**.  
  
|.NET Framework türü|Döndürülen dize|  
|-------------------------|---------------------|  
|Boole değeri|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Biçim "yyyy-aa-ddTHH:mm:sszzzzzz" ve onun alt kümeleri.|  
|Zaman aralığı|Biçimidir PnYnMnTnHnMnS diğer bir deyişle, `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika, ve 20 saniye süresidir.|  
  
> [!NOTE]
>  .NET Framework türlerinin herhangi biriyle dönüştürme kullanarak bir dize tablosunda listeleniyorsa **ToString** yöntemi, döndürülen dizeye temel tür, ancak XML Şeması (XSD) dize türü değil.  
  
 **DateTime** ve **Timespan** değer türü içinde farklı bir **DateTime** anlık süre içinde oysa temsil eder bir **TimeSpan** bir zaman aralığını temsil eder. **DateTime** ve **Timespan** biçimleri, XML Şeması (XSD) veri türleri belirtiminde belirtilir. Örneğin:  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 **Output**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 Aşağıdaki kod bir tamsayı bir dizeye dönüştürür:  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 **Output**  
  
 `<Number>200</Number>`  
  
 Ancak, bir dizeye dönüştürüyorsanız **Boole**, **tek**, veya **çift**, döndürülen .NET Framework türü kullanırken döndürülen tür ile aynı değil **System.Convert** sınıfı.  
  
## <a name="string-to-boolean"></a>Boole dizesi  
 Aşağıdaki tabloda, ne tür bir dizeye dönüştürürken verilen Giriş dizeleri için oluşturulur gösterilmektedir **Boole** kullanarak **ToBoolean** yöntemi.  
  
|Giriş parametresi geçerli bir dize|.NET framework çıktı türü|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 Örneğin, aşağıdaki XML verilen:  
  
 **Giriş**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 Her ikisi de aşağıdaki kodda, anlaşılabilir ve **bDeğer** olduğu **System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Tek bir dizeye  
 Aşağıdaki tabloda, ne tür bir dizeye dönüştürürken verilen Giriş dizeleri için oluşturulur gösterir bir **tek** kullanarak **ToSingle** yöntemi.  
  
|Giriş parametresi geçerli bir dize|.NET framework çıktı türü|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>Çift için dize  
 Aşağıdaki tabloda, ne tür bir dizeye dönüştürürken verilen Giriş dizeleri için oluşturulur gösterir bir **tek** kullanarak **ToDouble** yöntemi.  
  
|Giriş parametresi geçerli bir dize|.NET framework çıktı türü|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 Aşağıdaki kod yazma `<Infinity>INF</Infinity>`:  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Veri Türlerini Dönüştürme](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
- [.NET Framework Türlerini Dizelere Dönüştürme](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
