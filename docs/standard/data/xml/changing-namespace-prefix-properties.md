---
description: 'Daha fazla bilgi edinin: ad alanı öneki özelliklerini değiştirme'
title: Ad Alanı Ön Ek Özelliklerini Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: f6ca7d1c732f357a2c3ff8ba847d65314da81083
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99714007"
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
  
 **Çıktı**  
  
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
  
 **Çıktı**  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 Ağaç, belge çağrısının bir sonucu olarak bir dizeye kalıcı yapıldığında **. InnerXml**, `xmlns:a='123'` öğesinin ad alanını korumak için eklenmiştir `test` . İdi `'123'` ve kaldı `'123'` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
