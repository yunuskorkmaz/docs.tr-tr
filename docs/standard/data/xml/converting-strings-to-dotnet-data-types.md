---
title: ".NET Framework veri türleri için dizeleri dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce594234e601cd8feb4723bbc383db9e3ed40522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-strings-to-net-framework-data-types"></a>.NET Framework veri türleri için dizeleri dönüştürme
Bir dizeyi bir .NET Framework veri türüne dönüştürmek istiyorsanız, kullanmak **XmlConvert** uygulama gereksinimlerine uygun yöntemi. Kullanılabilir tüm dönüştürme yöntemleri listesi **XmlConvert** sınıfı için bkz: <xref:System.Xml.XmlConvert>.  
  
 Döndürülen dize **ToString** geçirilen verileri dize sürümü bir yöntemdir. Ayrıca, kullanarak Dönüştür çeşitli .NET Framework türleri vardır **XmlConvert** yöntemlere kullanmayın henüz sınıf **System.Convert'i** sınıfı. **XmlConvert** sınıf XML Şeması (XSD) veri türü izler ve bir veri, türü **XmlConvert** eşleyebilirsiniz.  
  
 Aşağıdaki tabloda, .NET Framework veri türleri ve XML Şeması (XSD) veri türü eşlemesi kullanarak döndürülen dize türlerini listeler. Bu .NET Framework türleri kullanılarak işlenemez **System.Convert'i**.  
  
|.NET Framework türü|Döndürülen dize|  
|-------------------------|---------------------|  
|Boole değeri|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Biçim "yyyy-aa-ddTHH:mm:sszzzzzz" ve onun alt kümeleri.|  
|TimeSpan|Biçimidir PnYnMnTnHnMnS diğer bir deyişle, `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika, ve 20 saniye süresince.|  
  
> [!NOTE]
>  .NET Framework türlerinden herhangi birini dönüştürme kullanarak bir dize için tabloda listelenen **ToString** yöntemi, döndürülen dize temel türü, ancak XML Şeması (XSD) dize türü değil.  
  
 **DateTime** ve **Timespan** değer türü içinde farklı bir **DateTime** ise, zaman içindeki bir anlık temsil eden bir **TimeSpan** bir zaman aralığı temsil eder. **DateTime** ve **Timespan** biçimleri XML Şeması (XSD) veri türleri belirtiminde belirtilir. Örneğin:  
  
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
  
 Aşağıdaki kod, tamsayı bir dizeye dönüştürür:  
  
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
  
 Ancak, bir dizeyi dönüştürüyorsanız **Boolean**, **tek**, veya **çift**, döndürülen .NET Framework türü kullanırken döndürülen tür ile aynı değil **System.Convert'i** sınıfı.  
  
## <a name="string-to-boolean"></a>Boole değeri bir dize  
 Aşağıdaki tabloda, ne tür verilen Giriş dizeleri için bir dizeye dönüştürme sırasında oluşturulan gösterilmektedir **Boolean** kullanarak **ToBoolean** yöntemi.  
  
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
  
 Her ikisi de aşağıdaki kodla anlaşılabilir ve **bDeğer** olan **System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Tek bir dize  
 Aşağıdaki tabloda, ne tür verilen Giriş dizeleri için bir dizeye dönüştürme sırasında oluşturulan gösterilmektedir bir **tek** kullanarak **ToSingle** yöntemi.  
  
|Giriş parametresi geçerli bir dize|.NET framework çıktı türü|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>Çift dizeye  
 Aşağıdaki tabloda, ne tür verilen Giriş dizeleri için bir dizeye dönüştürme sırasında oluşturulan gösterilmektedir bir **tek** kullanarak **ToDouble** yöntemi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML veri türlerini dönüştürme](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [.NET Framework türleri dizeleri dönüştürme](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
