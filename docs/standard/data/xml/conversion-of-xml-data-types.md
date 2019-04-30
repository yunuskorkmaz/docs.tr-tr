---
title: XML Veri Türlerini Dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56b5b51848858b7f1240059ca30eb48474650b73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669127"
---
# <a name="conversion-of-xml-data-types"></a>XML Veri Türlerini Dönüştürme
Yöntemlerin çoğunun bulunan bir **XmlConvert** sınıfı veri dizeler ve kesin tür belirtilmiş biçimleri arasında dönüştürmek için kullanılır. Yerel ayar bağımsız yöntemlerdir. Bu, tüm yerel ayarlar dönüştürme yaparken dikkate değil, anlamına gelir.  
  
## <a name="reading-string-as-types"></a>Okuma dize türleri olarak  
 Aşağıdaki örnek bir dize olarak okur ve ona dönüştürür bir **DateTime** türü.  
  
 Aşağıdaki XML geçirmesini:  
  
 **Giriş**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Bu kod dizeye dönüştürür **DateTime** biçimi:  
  
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
  
## <a name="writing-strings-as-types"></a>Yazma dize türleri olarak  
 Aşağıdaki örnek okuma bir **Int32** ve bir dizeye dönüştürür.  
  
 Aşağıdaki XML geçirmesini:  
  
 **Giriş**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Bu kod dönüştürür **Int32** içine bir **dize**:  
  
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
