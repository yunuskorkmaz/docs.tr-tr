---
title: Eleman adlarına nasıl filtre yapılır (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 74efb19ef5ec77ca29145d27a8e5aa977530b68b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141268"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a>Eleman adlarına nasıl filtre yapılır (LINQ - XML) (C#)
Döndürülen <xref:System.Collections.Generic.IEnumerable%601> yöntemlerden birini <xref:System.Xml.Linq.XElement>aradiğinizde, öğe adına filtre uygulayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, yalnızca belirtilen ada sahip torunları içerecek şekilde filtre uygulanmış bir soyundan gelenler koleksiyonunu alır.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 Koleksiyonların <xref:System.Xml.Linq.XElement> döndürülen <xref:System.Collections.Generic.IEnumerable%601> diğer yöntemleri de aynı şekilde izler. İmzaları benzer <xref:System.Xml.Linq.XContainer.Elements%2A> ve. <xref:System.Xml.Linq.XContainer.Descendants%2A> Benzer yöntem imzalarına sahip yöntemlerin tam listesi aşağıda verilmiştir:  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında Tipik Satın Alma Siparişi.](./sample-xml-file-typical-purchase-order-in-a-namespace.md)  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](./linq-to-xml-axes-overview.md)
