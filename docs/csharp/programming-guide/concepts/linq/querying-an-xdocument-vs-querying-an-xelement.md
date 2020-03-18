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
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="fbec2-102">XDocument ve XElement Sorgulama (C#) Sorgulama</span><span class="sxs-lookup"><span data-stu-id="fbec2-102">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="fbec2-103">Bir belgeyi <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>yüklediğinizde, 'den yüklediğinizden biraz daha farklı sorgular <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>yazmanız gerektiğini fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fbec2-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="fbec2-104">XDocument.Load ve XElement.Load Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="fbec2-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="fbec2-105">Bir XML belgesini bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>via'ya yüklediğinizde, <xref:System.Xml.Linq.XElement> XML ağacının kökünde yüklenen belgenin kök öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="fbec2-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="fbec2-106">Ancak, aynı XML belgesini bir <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>via'ya yüklediğinizde, <xref:System.Xml.Linq.XDocument> ağacın kökü bir düğümdür ve yüklenen belgenin <xref:System.Xml.Linq.XElement> kök öğesi <xref:System.Xml.Linq.XDocument>, 'nin alt düğümüne izin verilen öğedir.</span><span class="sxs-lookup"><span data-stu-id="fbec2-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="fbec2-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Eksenler kök düğümüne göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="fbec2-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="fbec2-108">Bu ilk örnek kullanarak <xref:System.Xml.Linq.XElement.Load%2A>bir XML ağacı yükler.</span><span class="sxs-lookup"><span data-stu-id="fbec2-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="fbec2-109">Daha sonra ağacın kök alt öğeleri için sorgular.</span><span class="sxs-lookup"><span data-stu-id="fbec2-109">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="fbec2-110">Beklendiği gibi, bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fbec2-110">As expected, this example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="fbec2-111">Aşağıdaki örnek, XML ağacının bir <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement>. yerine yüklenmesi dışında, yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="fbec2-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="fbec2-112">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fbec2-112">This example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="fbec2-113">Aynı sorgunun üç alt `Root` düğüm yerine bir düğümü döndürdene dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fbec2-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="fbec2-114">Bununla başa çıkmak için bir <xref:System.Xml.Linq.XDocument.Root%2A> yaklaşım aşağıdaki gibi, eksenler yöntemleri erişmeden önce özelliği kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="fbec2-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="fbec2-115">Bu sorgu şimdi ağaçta köklü sorgu olarak aynı <xref:System.Xml.Linq.XElement>şekilde gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="fbec2-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="fbec2-116">Örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fbec2-116">The example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  