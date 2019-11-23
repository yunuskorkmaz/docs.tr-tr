---
title: Bir XDocument sorgulama ve bir XElement sorgulama (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 4aba08319abeb21de79b3b8511044b8272402984
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834943"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>Bir XDocument sorgulama ve bir XElement sorgulama (Visual Basic)
<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>aracılığıyla bir belge yüklediğinizde, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>aracılığıyla yükleme yaparken sorguları biraz farklı yazmanız gerektiğini fark edeceksiniz.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument. Load ve XElement. Load karşılaştırması  
 Bir XML belgesini <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>aracılığıyla bir <xref:System.Xml.Linq.XElement> yüklediğinizde, XML ağacının kökündeki <xref:System.Xml.Linq.XElement> yüklenen belgenin kök öğesini içerir. Ancak, <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>aracılığıyla aynı XML belgesini bir <xref:System.Xml.Linq.XDocument> yüklediğinizde, ağacın kökü bir <xref:System.Xml.Linq.XDocument> düğümüdür ve yüklenen belgenin kök öğesi <xref:System.Xml.Linq.XDocument>izin verilen alt <xref:System.Xml.Linq.XElement> düğümüdür. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenleri kök düğüme göre çalışır.  
  
 Bu ilk örnek, <xref:System.Xml.Linq.XElement.Load%2A>kullanarak bir XML ağacı yükler. Daha sonra ağacın kök öğelerinin alt öğelerini sorgular.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Beklendiği gibi, bu örnek aşağıdaki çıktıyı üretir:  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Aşağıdaki örnek, XML ağacının bir <xref:System.Xml.Linq.XElement>yerine bir <xref:System.Xml.Linq.XDocument> yüklendiği özel durum ile yukarıdaki ile aynıdır.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Aynı sorgunun üç alt düğüm yerine bir `Root` düğümü döndürtiğine dikkat edin.  
  
 Bu ile ilgilenmeye yönelik bir yaklaşım, aşağıdaki gibi, eksen yöntemlerine erişmeden önce <xref:System.Xml.Linq.XDocument.Root%2A> özelliğini kullanmaktır:  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Bu sorgu artık <xref:System.Xml.Linq.XElement>kök ağaçtaki sorgu ile aynı şekilde gerçekleştirilir. Örnek aşağıdaki çıktıyı üretir:  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel sorgular (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
