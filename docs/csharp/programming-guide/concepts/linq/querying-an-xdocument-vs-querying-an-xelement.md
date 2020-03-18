---
title: XDocument ve XElement Sorgulama (C#) Sorgulama
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 475c77934ad535bad9ef79ff58bbddf991dc8f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253134"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>XDocument ve XElement Sorgulama (C#) Sorgulama
Bir belgeyi <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>yüklediğinizde, 'den yüklediğinizden biraz daha farklı sorgular <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>yazmanız gerektiğini fark edeceksiniz.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument.Load ve XElement.Load Karşılaştırması  
 Bir XML belgesini bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>via'ya yüklediğinizde, <xref:System.Xml.Linq.XElement> XML ağacının kökünde yüklenen belgenin kök öğesini içerir. Ancak, aynı XML belgesini bir <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>via'ya yüklediğinizde, <xref:System.Xml.Linq.XDocument> ağacın kökü bir düğümdür ve yüklenen belgenin <xref:System.Xml.Linq.XElement> kök öğesi <xref:System.Xml.Linq.XDocument>, 'nin alt düğümüne izin verilen öğedir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Eksenler kök düğümüne göre çalışır.  
  
 Bu ilk örnek kullanarak <xref:System.Xml.Linq.XElement.Load%2A>bir XML ağacı yükler. Daha sonra ağacın kök alt öğeleri için sorgular.  
  
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
  
 Beklendiği gibi, bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Aşağıdaki örnek, XML ağacının bir <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement>. yerine yüklenmesi dışında, yukarıdakiyle aynıdır.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Aynı sorgunun üç alt `Root` düğüm yerine bir düğümü döndürdene dikkat edin.  
  
 Bununla başa çıkmak için bir <xref:System.Xml.Linq.XDocument.Root%2A> yaklaşım aşağıdaki gibi, eksenler yöntemleri erişmeden önce özelliği kullanmaktır:  
  
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
  
 Bu sorgu şimdi ağaçta köklü sorgu olarak aynı <xref:System.Xml.Linq.XElement>şekilde gerçekleştirir. Örnek aşağıdaki çıktıyı üretir:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  