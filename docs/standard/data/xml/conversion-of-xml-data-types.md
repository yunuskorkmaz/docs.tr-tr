---
title: XML Veri Türlerini Dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b0cdab8861ca50b40ce2b422fcc1acf16e2f2273
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711096"
---
# <a name="conversion-of-xml-data-types"></a>XML Veri Türlerini Dönüştürme
Bir **XmlConvert** sınıfında bulunan yöntemlerin çoğu, dizeler ve kesin türü belirtilmiş biçimler arasında veri dönüştürmek için kullanılır. Yöntemler yerel olarak bağımsızdır. Bu, dönüştürme yaparken herhangi bir yerel ayarı dikkate almaz demektir.  
  
## <a name="reading-string-as-types"></a>Dize tür olarak okunuyor  
 Aşağıdaki örnek bir dize okur ve bunu bir **Tarih saat** türüne dönüştürür.  
  
 Aşağıdaki XML girişi verildi:  
  
 **Giriş**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Bu kod, dizeyi **Tarih saat** biçimine dönüştürür:  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a>Dizeleri tür olarak yazma  
 Aşağıdaki örnek bir **Int32** okur ve bunu bir dizeye dönüştürür.  
  
 Aşağıdaki XML girişi verildi:  
  
 **Giriş**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Bu kod, **Int32** 'Yi bir **dizeye**dönüştürür:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Veri Türleri için Dizeleri Dönüştürme](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [.NET Framework Türlerini Dizelere Dönüştürme](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
