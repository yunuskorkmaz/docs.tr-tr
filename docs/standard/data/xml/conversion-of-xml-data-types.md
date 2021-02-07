---
description: 'Daha fazla bilgi edinin: XML veri türlerini dönüştürme'
title: XML Veri Türlerini Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: 7f7657f3ee290ff88dff1ef869a723c947cbce5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713955"
---
# <a name="conversion-of-xml-data-types"></a>XML Veri Türlerini Dönüştürme

**XmlConvert** sınıfında bulunan yöntemlerin çoğu, dizeleri ve kesin belirlenmiş biçimleri arasında veri dönüştürmek için kullanılır. Yöntemler yerel olarak bağımsızdır. Bu, dönüştürme yaparken herhangi bir yerel ayarı dikkate almaz demektir.  
  
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
  
 Bu kod, **Int32** 'Yi bir **dizeye** dönüştürür:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Veri Türleri için Dizeleri Dönüştürme](converting-strings-to-dotnet-data-types.md)
- [.NET Framework Türlerini Dizelere Dönüştürme](converting-dotnet-types-to-strings.md)
