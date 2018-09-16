---
title: Namespace ön ek özelliklerini değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6597a3a57cd68c4dd17c4fbae882590f373709
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674305"
---
# <a name="changing-namespace-prefix-properties"></a>Namespace ön ek özelliklerini değiştirme
**XmlNode** sınıfı belirli bir düğümle ilişkili ad alanı öneki değiştirmenize izin verir. Örneğin, aşağıdaki kod, değişmekte olan bir öğenin ön ek gösterir.  
  
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
  
 Bir düğümün önek değiştirme, ad alanı değiştirmez. Ad alanı, yalnızca düğüm oluşturulduğunda ayarlanabilir. Ağaç kalıcı, yeni ad alanı öznitelikleri kullanıma ayarladığınız ön ekini karşılamak için kalıcı. Yeni ad alanı oluşturulamazsa önek yerel adı ve ad alanı düğümü korur şekilde değiştirilir. Aşağıdaki örnek, eklenen bir ad alanı özniteliği gösterir.  
  
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
  
 Ne zaman ağaç kalıcı bir dizeye çağrısının sonucunda **belge. Sınıfının InnerXml**, `xmlns:a='123'` öznitelik ad alanı korumak için eklenen `test` öğesi. Bu `'123'`, ve onu kaldığını `'123'`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
