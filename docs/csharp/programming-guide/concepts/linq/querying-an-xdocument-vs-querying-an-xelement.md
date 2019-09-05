---
title: XDocument Sorgulama ve XElement (C#) sorgulama
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 475c77934ad535bad9ef79ff58bbddf991dc8f5c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253134"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>XDocument Sorgulama ve XElement (C#) sorgulama
Aracılığıyla <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>bir belge yüklediğinizde, ile <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>yükleme yaparken sorguları biraz farklı yazacağınız fark edeceksiniz.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument. Load ve XElement. Load karşılaştırması  
 Bir <xref:System.Xml.Linq.XElement> XML belgesini aracılığıyla <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>yüklediğinizde, <xref:System.Xml.Linq.XElement> xml ağacının kök öğesi yüklenen belgenin kök öğesini içerir. Ancak <xref:System.Xml.Linq.XDocument> , bir <xref:System.Xml.Linq.XDocument>ile <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>aynı XML belgesini yüklediğinizde, ağacın kökü bir <xref:System.Xml.Linq.XDocument> düğümdür ve yüklenen belgenin kök öğesi, öğesinin izin verilen alt <xref:System.Xml.Linq.XElement> düğümüdür. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Eksenler kök düğüme göre çalışır.  
  
 Bu ilk örnek kullanarak <xref:System.Xml.Linq.XElement.Load%2A>bir XML ağacı yükler. Daha sonra ağacın kök öğelerinin alt öğelerini sorgular.  
  
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
  
 Aşağıdaki örnek, xml ağacının bir <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement>yerine bir olarak yüklendiği özel durum ile, yukarıdaki bir ile aynıdır.  
  
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
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Aynı sorgunun üç alt düğüm yerine bir `Root` düğümü döndürtiğine dikkat edin.  
  
 Bu ile ilgilenmeye yönelik bir yaklaşım, aşağıdaki gibi <xref:System.Xml.Linq.XDocument.Root%2A> , eksen yöntemlerine erişmeden önce özelliğini kullanmaktır:  
  
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
  
 Bu sorgu artık, içinde <xref:System.Xml.Linq.XElement>kök ağaçtaki sorgu ile aynı şekilde gerçekleştirilir. Örnek aşağıdaki çıktıyı üretir:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  