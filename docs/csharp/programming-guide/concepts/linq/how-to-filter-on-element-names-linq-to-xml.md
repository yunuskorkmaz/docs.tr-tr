---
title: "Nasıl yapılır: öğe adları (LINQ-XML) filtresini (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d65dd8263ae178f47ba5556c7da7788ac88b393
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a>Nasıl yapılır: öğe adları (LINQ-XML) filtresini (C#)
Çağırdığınızda dönüş yöntemlerden birini <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, öğe adı filtreleyebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek yalnızca belirtilen ada sahip alt öğeleri içerecek şekilde filtre uygulanan bir alt koleksiyonunu alır.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 Dönüş diğer yöntemleri <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> koleksiyonları aynı düzeni izleyin. Kendi imzaları benzer <xref:System.Xml.Linq.XContainer.Elements%2A> ve <xref:System.Xml.Linq.XContainer.Descendants%2A>. Benzer yöntemi imzalara sahip olduğunu yöntemlerinin tam listesi verilmiştir:  
  
-   <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir. Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: bir Namespace tipik satınalma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
