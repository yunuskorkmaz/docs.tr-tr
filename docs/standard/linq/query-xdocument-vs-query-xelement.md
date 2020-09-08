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
# <a name="query-an-xdocument-vs-query-an-xelement-linq-to-xml"></a><span data-ttu-id="e6b32-103">Sorgu a `XDocument` ile sorgu a `XElement` (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e6b32-103">Query an `XDocument` vs. query an `XElement` (LINQ to XML)</span></span>

<span data-ttu-id="e6b32-104">Kullanarak bir belgeyi yüklediğinizde yazdığınız sorgu, <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> ile yüklerken yazdıklarından farklı bir kaydıktı <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e6b32-104">The query you write when you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> differs slighty from what you write when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>

## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="e6b32-105">Ve karşılaştırması `XDocument.Load``XElement.Load`</span><span class="sxs-lookup"><span data-stu-id="e6b32-105">Comparison of `XDocument.Load` and `XElement.Load`</span></span>

<span data-ttu-id="e6b32-106">Bir XML belgesini <xref:System.Xml.Linq.XElement> aracılığıyla yüklediğinizde <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XElement> XML ağacının kök öğesi yüklenen belgenin kök öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e6b32-106">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="e6b32-107">Ancak, bir ile aynı XML belgesini yüklediğinizde <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , ağacın kökü bir <xref:System.Xml.Linq.XDocument> düğümdür ve yüklenen belgenin kök öğesi, öğesinin izin verilen alt <xref:System.Xml.Linq.XElement> düğümüdür <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="e6b32-107">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="e6b32-108">LINQ to XML eksenleri kök düğüme göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="e6b32-108">The LINQ to XML axes operate relative to the root node.</span></span>

## <a name="example-load-an-xml-tree-using-xelementload-then-query-for-child-elements"></a><span data-ttu-id="e6b32-109">Örnek: kullanarak bir XML ağacı yükleme `XElement.Load` , sonra alt öğeleri sorgula</span><span class="sxs-lookup"><span data-stu-id="e6b32-109">Example: Load an XML tree using `XElement.Load`, then query for child elements</span></span>

<span data-ttu-id="e6b32-110">Bu ilk örnek kullanarak bir XML ağacı yükler <xref:System.Xml.Linq.XElement.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="e6b32-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="e6b32-111">Daha sonra ağacın kök öğelerinin alt öğelerini sorgular.</span><span class="sxs-lookup"><span data-stu-id="e6b32-111">It then queries for the child elements of the root of the tree.</span></span>

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

<span data-ttu-id="e6b32-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e6b32-112">This example produces the following output:</span></span>

```output
Querying tree loaded with XElement.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```

## <a name="example-load-an-xml-tree-using-xdocumentload-then-query-for-child-elements"></a><span data-ttu-id="e6b32-113">Örnek: kullanarak bir XML ağacı yükleme `XDocument.Load` , sonra alt öğeleri sorgula</span><span class="sxs-lookup"><span data-stu-id="e6b32-113">Example: Load an XML tree using `XDocument.Load`, then query for child elements</span></span>

<span data-ttu-id="e6b32-114">Sonraki örnek, yukarıdaki ile aynı şekilde, ancak XML ağacı bir yerine bir olarak yüklenmiştir <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="e6b32-114">The next example does the same as the one above, but the XML tree has been loaded into an <xref:System.Xml.Linq.XDocument>, rather than an <xref:System.Xml.Linq.XElement>.</span></span>

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

<span data-ttu-id="e6b32-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e6b32-115">This example produces the following output:</span></span>

```output
Querying tree loaded with XDocument.Load
----
<Root>
  <Child1>1</Child1>
  <Child2>2</Child2>
  <Child3>3</Child3>
</Root>
```

<span data-ttu-id="e6b32-116">Aynı sorgunun `Root` üç alt düğüm yerine bir düğümü döndürtiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e6b32-116">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>

<span data-ttu-id="e6b32-117">Bu ile ilgilenmeye yönelik bir yaklaşım <xref:System.Xml.Linq.XDocument.Root%2A> , aşağıdaki gibi, eksen yöntemlerine erişmeden önce özelliğini kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="e6b32-117">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>

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

<span data-ttu-id="e6b32-118">Bu sorgu artık, içinde kök ağaçtaki sorgu ile aynı şekilde gerçekleştirilir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="e6b32-118">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span>

<span data-ttu-id="e6b32-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e6b32-119">This example produces the following output:</span></span>

```output
Querying tree loaded with XDocument.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```
