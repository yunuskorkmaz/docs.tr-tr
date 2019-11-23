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
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="4e41a-102">Bir XDocument sorgulama ve bir XElement sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e41a-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="4e41a-103"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>aracılığıyla bir belge yüklediğinizde, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>aracılığıyla yükleme yaparken sorguları biraz farklı yazmanız gerektiğini fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="4e41a-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="4e41a-104">XDocument. Load ve XElement. Load karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="4e41a-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="4e41a-105">Bir XML belgesini <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>aracılığıyla bir <xref:System.Xml.Linq.XElement> yüklediğinizde, XML ağacının kökündeki <xref:System.Xml.Linq.XElement> yüklenen belgenin kök öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4e41a-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="4e41a-106">Ancak, <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>aracılığıyla aynı XML belgesini bir <xref:System.Xml.Linq.XDocument> yüklediğinizde, ağacın kökü bir <xref:System.Xml.Linq.XDocument> düğümüdür ve yüklenen belgenin kök öğesi <xref:System.Xml.Linq.XDocument>izin verilen alt <xref:System.Xml.Linq.XElement> düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="4e41a-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="4e41a-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenleri kök düğüme göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="4e41a-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="4e41a-108">Bu ilk örnek, <xref:System.Xml.Linq.XElement.Load%2A>kullanarak bir XML ağacı yükler.</span><span class="sxs-lookup"><span data-stu-id="4e41a-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="4e41a-109">Daha sonra ağacın kök öğelerinin alt öğelerini sorgular.</span><span class="sxs-lookup"><span data-stu-id="4e41a-109">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="4e41a-110">Beklendiği gibi, bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4e41a-110">As expected, this example produces the following output:</span></span>  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="4e41a-111">Aşağıdaki örnek, XML ağacının bir <xref:System.Xml.Linq.XElement>yerine bir <xref:System.Xml.Linq.XDocument> yüklendiği özel durum ile yukarıdaki ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4e41a-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="4e41a-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4e41a-112">This example produces the following output:</span></span>  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="4e41a-113">Aynı sorgunun üç alt düğüm yerine bir `Root` düğümü döndürtiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4e41a-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="4e41a-114">Bu ile ilgilenmeye yönelik bir yaklaşım, aşağıdaki gibi, eksen yöntemlerine erişmeden önce <xref:System.Xml.Linq.XDocument.Root%2A> özelliğini kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="4e41a-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="4e41a-115">Bu sorgu artık <xref:System.Xml.Linq.XElement>kök ağaçtaki sorgu ile aynı şekilde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4e41a-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="4e41a-116">Örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4e41a-116">The example produces the following output:</span></span>  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e41a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e41a-117">See also</span></span>

- [<span data-ttu-id="4e41a-118">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e41a-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
