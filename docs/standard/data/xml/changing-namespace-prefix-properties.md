---
title: Ad Alanı Ön Ek Özelliklerini Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: e6b811d58ef9d98c51e9a45a46a1965c4fa12b55
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711122"
---
# <a name="changing-namespace-prefix-properties"></a>Ad Alanı Ön Ek Özelliklerini Değiştirme
**XMLNode** sınıfı, belirli bir düğümle ilişkili ad alanı önekini değiştirmenize izin verir. Örneğin, aşağıdaki kod değiştirilmekte olan bir öğenin önekini gösterir.  
  
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
  
 Bir düğümün önekini değiştirmek, ad alanını değiştirmez. Ad alanı yalnızca düğüm oluşturulduğunda ayarlanabilir. Ağacı kalıcı hale getirdikten sonra, ayarladığınız ön eki karşılamak için yeni ad alanı öznitelikleri kalıcı olabilir. Yeni ad alanı oluşturuoluşturulamadığı takdirde, düğüm yerel adını ve ad alanını koruyabilmesi için önek değişir. Aşağıdaki örnekte, eklenmekte olan bir ad alanı özniteliği gösterilmektedir.  
  
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
  
 Ağaç, belge çağrısının bir sonucu olarak bir dizeye kalıcı yapıldığında **. InnerXml**, `test` öğesinin ad alanını korumak için `xmlns:a='123'` özniteliği eklenmiştir. `'123'`ve `'123'`kaldı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
