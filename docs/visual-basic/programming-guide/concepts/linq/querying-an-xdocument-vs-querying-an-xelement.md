---
title: XDocument Sorgulama ve (Visual Basic) XElement sorgulama karşılaştırması
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 500b1e58663ef6aca052850ad7994687e2cc36f4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817727"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="b462a-102">XDocument Sorgulama ve (Visual Basic) XElement sorgulama karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="b462a-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="b462a-103">Bir belge aracılığıyla yüklediğinizde <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, sorguları aracılığıyla yüklediğinizde biraz farklı yazma olduğunu fark edeceksiniz <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b462a-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="b462a-104">XDocument.Load ve XElement.Load karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="b462a-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="b462a-105">Bir XML belgesine yüklediğinizde bir <xref:System.Xml.Linq.XElement> aracılığıyla <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> XML kökünde yüklenen belge kök öğesi ağacı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b462a-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="b462a-106">Ancak, yükleme sonrasında aynı XML belgeye bir <xref:System.Xml.Linq.XDocument> aracılığıyla <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, ağacının kökü olan bir <xref:System.Xml.Linq.XDocument> düğüm ve yüklenen belge kök öğesi olan bir izin verilen alt <xref:System.Xml.Linq.XElement> düğümünün <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="b462a-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="b462a-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Eksen kök düğümü göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="b462a-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="b462a-108">Bu ilk örnekte kullanarak bir XML ağacı yükler <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="b462a-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="b462a-109">Ardından ağacının kökü alt öğeleri için sorgular.</span><span class="sxs-lookup"><span data-stu-id="b462a-109">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="b462a-110">Beklendiği gibi bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b462a-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="b462a-111">Yukarıdakilerden biri XML ağacı yüklenen özel durumla aynı aşağıdaki örnek, bir <xref:System.Xml.Linq.XDocument> yerine bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b462a-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="b462a-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b462a-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="b462a-113">Aynı sorgu bir verdiğini fark `Root` üç alt düğümler yerine düğüm.</span><span class="sxs-lookup"><span data-stu-id="b462a-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="b462a-114">Bu ilgilenmek için bir yaklaşım ise kullanılacak <xref:System.Xml.Linq.XDocument.Root%2A> eksenleri yöntemleri gibi erişmeden önce özelliği:</span><span class="sxs-lookup"><span data-stu-id="b462a-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="b462a-115">Bu sorgu, sorgu ağaç kökü olarak artık aynı şekilde gerçekleştirir. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b462a-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b462a-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b462a-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b462a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b462a-117">See also</span></span>

- [<span data-ttu-id="b462a-118">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b462a-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
