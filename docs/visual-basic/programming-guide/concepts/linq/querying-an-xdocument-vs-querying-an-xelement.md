---
title: XDocument Sorgulama ve XElement Sorgulama Karşılaştırması
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 3cd79c8f2cde101de43a9b9e983709e2e0d11814
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396304"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="578ea-102">Bir XDocument sorgulama ve bir XElement sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="578ea-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="578ea-103">Aracılığıyla bir belge yüklediğinizde <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , ile yükleme yaparken sorguları biraz farklı yazacağınız fark edeceksiniz <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="578ea-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="578ea-104">XDocument. Load ve XElement. Load karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="578ea-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="578ea-105">Bir XML belgesini <xref:System.Xml.Linq.XElement> aracılığıyla yüklediğinizde <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XElement> XML ağacının kök öğesi yüklenen belgenin kök öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="578ea-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="578ea-106">Ancak, bir ile aynı XML belgesini yüklediğinizde <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , ağacın kökü bir <xref:System.Xml.Linq.XDocument> düğümdür ve yüklenen belgenin kök öğesi, öğesinin izin verilen alt <xref:System.Xml.Linq.XElement> düğümüdür <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="578ea-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="578ea-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Eksenler kök düğüme göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="578ea-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="578ea-108">Bu ilk örnek kullanarak bir XML ağacı yükler <xref:System.Xml.Linq.XElement.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="578ea-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="578ea-109">Daha sonra ağacın kök öğelerinin alt öğelerini sorgular.</span><span class="sxs-lookup"><span data-stu-id="578ea-109">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="578ea-110">Beklendiği gibi, bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="578ea-110">As expected, this example produces the following output:</span></span>  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="578ea-111">Aşağıdaki örnek, XML ağacının bir yerine bir olarak yüklendiği özel durum ile, yukarıdaki bir ile aynıdır <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="578ea-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="578ea-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="578ea-112">This example produces the following output:</span></span>  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="578ea-113">Aynı sorgunun `Root` üç alt düğüm yerine bir düğümü döndürtiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="578ea-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="578ea-114">Bu ile ilgilenmeye yönelik bir yaklaşım <xref:System.Xml.Linq.XDocument.Root%2A> , aşağıdaki gibi, eksen yöntemlerine erişmeden önce özelliğini kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="578ea-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="578ea-115">Bu sorgu artık, içinde kök ağaçtaki sorgu ile aynı şekilde gerçekleştirilir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="578ea-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="578ea-116">Örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="578ea-116">The example produces the following output:</span></span>  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="578ea-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="578ea-117">See also</span></span>

- [<span data-ttu-id="578ea-118">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="578ea-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
