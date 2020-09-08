---
title: Bir XDocument ile sorgu sorgulama-LINQ to XML bir XElement-
description: XDocument. Load ve XElement. Load tarafından yüklenen XML belgeleri için biraz farklı sorgular yazın.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 96d706bcc1871c9e420bafd984d08ca9616b5c18
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553894"
---
# <a name="query-an-xdocument-vs-query-an-xelement-linq-to-xml"></a>Sorgu a `XDocument` ile sorgu a `XElement` (LINQ to XML)

Kullanarak bir belgeyi yüklediğinizde yazdığınız sorgu, <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> ile yüklerken yazdıklarından farklı bir kaydıktı <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .

## <a name="comparison-of-xdocumentload-and-xelementload"></a>Ve karşılaştırması `XDocument.Load``XElement.Load`

Bir XML belgesini <xref:System.Xml.Linq.XElement> aracılığıyla yüklediğinizde <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XElement> XML ağacının kök öğesi yüklenen belgenin kök öğesini içerir. Ancak, bir ile aynı XML belgesini yüklediğinizde <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , ağacın kökü bir <xref:System.Xml.Linq.XDocument> düğümdür ve yüklenen belgenin kök öğesi, öğesinin izin verilen alt <xref:System.Xml.Linq.XElement> düğümüdür <xref:System.Xml.Linq.XDocument> . LINQ to XML eksenleri kök düğüme göre çalışır.

## <a name="example-load-an-xml-tree-using-xelementload-then-query-for-child-elements"></a>Örnek: kullanarak bir XML ağacı yükleme `XElement.Load` , sonra alt öğeleri sorgula

Bu ilk örnek kullanarak bir XML ağacı yükler <xref:System.Xml.Linq.XElement.Load%2A> . Daha sonra ağacın kök öğelerinin alt öğelerini sorgular.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
Querying tree loaded with XElement.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```

## <a name="example-load-an-xml-tree-using-xdocumentload-then-query-for-child-elements"></a>Örnek: kullanarak bir XML ağacı yükleme `XDocument.Load` , sonra alt öğeleri sorgula

Sonraki örnek, yukarıdaki ile aynı şekilde, ancak XML ağacı bir yerine bir olarak yüklenmiştir <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> .

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

```output
Querying tree loaded with XDocument.Load
----
<Root>
  <Child1>1</Child1>
  <Child2>2</Child2>
  <Child3>3</Child3>
</Root>
```

Aynı sorgunun `Root` üç alt düğüm yerine bir düğümü döndürtiğine dikkat edin.

Bu ile ilgilenmeye yönelik bir yaklaşım <xref:System.Xml.Linq.XDocument.Root%2A> , aşağıdaki gibi, eksen yöntemlerine erişmeden önce özelliğini kullanmaktır:

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

Bu sorgu artık, içinde kök ağaçtaki sorgu ile aynı şekilde gerçekleştirilir <xref:System.Xml.Linq.XElement> .

Bu örnek aşağıdaki çıktıyı üretir:

```output
Querying tree loaded with XDocument.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```
