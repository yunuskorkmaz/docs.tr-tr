---
title: Namespace önek özelliklerini değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3f41ba7281d67cc2ce848597926f5efebf4d489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="changing-namespace-prefix-properties"></a>Namespace önek özelliklerini değiştirme
**XmlNode** sınıfı belirli bir düğümle ilişkilendirilen ad alanı öneki değiştirmenize izin verir. Örneğin, aşağıdaki kod, bir öğenin değiştirilmesini önek gösterir.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Output**  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 Bir düğümün önek değiştirmek kendi ad değiştirmez. Ad yalnızca düğüm oluşturulduğunda ayarlayabilirsiniz. Ağaç kalır, yeni ad alanı öznitelikler çıkışı ayarladığınız önek karşılamak için kalıcı. Yeni ad alanı oluşturulamazsa düğüm kendi yerel ve ad alanına korur şekilde önek değiştirilir. Aşağıdaki örnek eklenmekte olan bir ad özniteliği gösterir.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Output**  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 Ne zaman ağaç kalıcı bir dizeye çağrısı sonucunda **belge. InnerXml**, `xmlns:a='123'` özniteliği ad alanını korumak için eklenmiştir `test` öğesi. Bu `'123'`, ve bunu kalan `'123'`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
