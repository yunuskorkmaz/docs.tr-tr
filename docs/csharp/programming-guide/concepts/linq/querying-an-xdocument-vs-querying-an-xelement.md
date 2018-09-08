---
title: XDocument sorgulama. (C#) XElement sorgulama karşılaştırması
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 991cbf14fde1c2e3e1e76ef10066db3408ca51c5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44127978"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>XDocument sorgulama. (C#) XElement sorgulama karşılaştırması
Bir belge aracılığıyla yüklediğinizde <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, sorguları aracılığıyla yüklediğinizde biraz farklı yazma olduğunu fark edeceksiniz <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument.Load ve XElement.Load karşılaştırması  
 Bir XML belgesine yüklediğinizde bir <xref:System.Xml.Linq.XElement> aracılığıyla <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> XML kökünde yüklenen belge kök öğesi ağacı içeriyor. Ancak, yükleme sonrasında aynı XML belgeye bir <xref:System.Xml.Linq.XDocument> aracılığıyla <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, ağacının kökü olan bir <xref:System.Xml.Linq.XDocument> düğüm ve yüklenen belge kök öğesi olan bir izin verilen alt <xref:System.Xml.Linq.XElement> düğümünün <xref:System.Xml.Linq.XDocument>. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Eksen kök düğümü göre çalışır.  
  
 Bu ilk örnekte kullanarak bir XML ağacı yükler <xref:System.Xml.Linq.XElement.Load%2A>. Ardından ağacının kökü alt öğeleri için sorgular.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Beklendiği gibi bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Yukarıdakilerden biri XML ağacı yüklenen özel durumla aynı aşağıdaki örnek, bir <xref:System.Xml.Linq.XDocument> yerine bir <xref:System.Xml.Linq.XElement>.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Aynı sorgu bir verdiğini fark `Root` üç alt düğümler yerine düğüm.  
  
 Bu ilgilenmek için bir yaklaşım ise kullanılacak <xref:System.Xml.Linq.XDocument.Root%2A> eksenleri yöntemleri gibi erişmeden önce özelliği:  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Bu sorgu, sorgu ağaç kökü olarak artık aynı şekilde gerçekleştirir. <xref:System.Xml.Linq.XElement>. Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Temel sorgular (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
