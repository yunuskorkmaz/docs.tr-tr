---
title: "XML veri türlerini dönüştürme"
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
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a>XML veri türlerini dönüştürme
Yöntemleri çoğunluğu bulunan bir **XmlConvert** sınıfı, dizeleri ve kesin türü belirtilmiş biçimleri arasında veri dönüştürmek için kullanılır. Yerel ayar bağımsız yöntemleridir. Bu, bunlar herhangi bir yerel ayarı dönüştürme yapılırken dikkate değil, anlamına gelir.  
  
## <a name="reading-string-as-types"></a>Okuma dize türleri olarak  
 Aşağıdaki örnek bir dize okur ve ona dönüştüren bir **DateTime** türü.  
  
 Aşağıdaki XML giriş verilen:  
  
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
  
 Aşağıdaki XML giriş verilen:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework veri türleri için dizeleri dönüştürme](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [.NET Framework türleri dizeleri dönüştürme](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
