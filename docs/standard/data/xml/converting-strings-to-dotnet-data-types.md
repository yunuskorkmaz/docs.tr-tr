---
title: .NET Framework Veri Türleri için Dizeleri Dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: fda5441c58d14b91a9eca16fff9149c8795f95b9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289232"
---
# <a name="converting-strings-to-net-framework-data-types"></a>.NET Framework Veri Türleri için Dizeleri Dönüştürme
Bir dizeyi .NET Framework veri türüne dönüştürmek istiyorsanız, uygulama gereksinimlerine uyan **XmlConvert** yöntemini kullanın. **XmlConvert** sınıfında bulunan tüm dönüştürme yöntemlerinin listesi için bkz <xref:System.Xml.XmlConvert> ..  
  
 **ToString** yönteminden döndürülen dize, geçirilen verilerin dize bir sürümüdür. Ayrıca, **XmlConvert** sınıfını kullanarak dönüştüren birkaç .NET Framework türü vardır ancak **System. Convert** sınıfındaki yöntemleri kullanmaz. **XmlConvert** sınıfı, XML ŞEMASı (xsd) veri türü belirtimini Izler ve **XmlConvert** 'in eşleyebileceğiniz bir veri türüne sahiptir.  
  
 Aşağıdaki tabloda .NET Framework veri türleri ve XML şeması (XSD) veri türü eşlemesi kullanılarak döndürülen dize türleri listelenmektedir. Bu .NET Framework türleri **System. Convert**kullanılarak işlenemiyor.  
  
|.NET Framework türü|Döndürülen dize|  
|-------------------------|---------------------|  
|Boole|"true", "false"|  
|Single. PositiveInfinity|'SI|  
|Tek. NegativeInfinity|"-INF"|  
|Double. PositiveInfinity|'SI|  
|Double. NegativeInfinity|"-INF"|  
|DateTime|Biçim "yyyy-MM-ddTHH: mm: sszzzzzz" ve alt kümeleridir.|  
|Timespan|Biçim, `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika ve 20 saniye olmak üzere Pnazmntnhnmns 'dir|  
  
> [!NOTE]
> Tabloda listelenen .NET Framework türlerinden herhangi birini **ToString** yöntemini kullanarak bir dizeye dönüştürürseniz, döndürülen dize temel tür değildir, ancak XML ŞEMASı (xsd) dize türüdür.  
  
 **DateTime** ve **TimeSpan** değer türü, bir **Tarih** saat içinde anlık bir zaman aralığını temsil ettiğinden, bir **TimeSpan** değeri bir zaman aralığı temsil ettiğinden farklılık gösterir. **DateTime** ve **TIMESPAN** biçimleri, XML şeması (xsd) veri türleri belirtiminde belirtilir. Örneğin:  
  
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
  
 **Çıktı**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 Aşağıdaki kod bir tamsayıyı bir dizeye dönüştürür:  
  
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
  
 **Çıktı**  
  
 `<Number>200</Number>`  
  
 Ancak, bir dizeyi **Boolean**, **Single**veya **Double**'A dönüştürüyorsanız döndürülen .NET Framework türü, **System. Convert** sınıfı kullanılırken döndürülen türle aynı değildir.  
  
## <a name="string-to-boolean"></a>Boole olarak dize  
 Aşağıdaki tabloda, **ToBoolean** yöntemi kullanılarak bir dize **Boole** değerine dönüştürülürken, verilen giriş dizeleri için hangi türün oluşturulduğu gösterilmektedir.  
  
|Geçerli dize giriş parametresi|.NET Framework çıkış türü|  
|----------------------------------|--------------------------------|  
|değeri|Boolean. true|  
|"1"|Boolean. true|  
|yanlýþ|Boolean. false|  
|"0"|Boolean. false|  
  
 Örneğin, aşağıdaki XML verildiğinde:  
  
 **Giriş**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 Her ikisi de aşağıdaki kod tarafından Anlaşılabiliyorsa, **bValue** ise **System. Boolean. true**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Dizeden tek  
 Aşağıdaki tabloda, bir dizeyi **ToSingle** yöntemi kullanılarak **tek tek** dönüştürme sırasında verilen giriş dizeleri için oluşturulan tür gösterilmektedir.  
  
|Geçerli dize giriş parametresi|.NET Framework çıkış türü|  
|----------------------------------|--------------------------------|  
|'SI|Single. PositiveInfinity|  
|"-INF"|Tek. NegativeInfinity|  
  
## <a name="string-to-double"></a>Double için dize  
 Aşağıdaki tabloda, **ToDouble** yöntemi kullanılarak bir dizeyi **tek tek** dönüştürmek için verilen giriş dizeleri için hangi türün oluşturulduğu gösterilmektedir.  
  
|Geçerli dize giriş parametresi|.NET Framework çıkış türü|  
|----------------------------------|--------------------------------|  
|'SI|Double. PositiveInfinity|  
|"-INF"|Double. NegativeInfinity|  
  
 Aşağıdaki kod yazılır `<Infinity>INF</Infinity>` :  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Veri Türlerini Dönüştürme](conversion-of-xml-data-types.md)
- [.NET Framework Türlerini Dizelere Dönüştürme](converting-dotnet-types-to-strings.md)
