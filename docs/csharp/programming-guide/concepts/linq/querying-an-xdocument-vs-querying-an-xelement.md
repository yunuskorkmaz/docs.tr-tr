---
title: Bir XDocument sorgulama ve XElement sorgulama (C#)
description: Bir XDocument sorgulama ve bir XElement sorgulama arasındaki farklar hakkında bilgi edinin. Bu farklılıkları gösteren kod örneklerini gözden geçirin.
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 0c81768f06148308a639f96f4041e464b24edd33
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300325"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="e7019-104">Bir XDocument sorgulama ve XElement sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="e7019-104">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="e7019-105">Aracılığıyla bir belge yüklediğinizde <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , ile yükleme yaparken sorguları biraz farklı yazacağınız fark edeceksiniz <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e7019-105">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="e7019-106">XDocument. Load ve XElement. Load karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="e7019-106">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="e7019-107">Bir XML belgesini <xref:System.Xml.Linq.XElement> aracılığıyla yüklediğinizde <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XElement> XML ağacının kök öğesi yüklenen belgenin kök öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e7019-107">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="e7019-108">Ancak, bir ile aynı XML belgesini yüklediğinizde <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , ağacın kökü bir <xref:System.Xml.Linq.XDocument> düğümdür ve yüklenen belgenin kök öğesi, öğesinin izin verilen alt <xref:System.Xml.Linq.XElement> düğümüdür <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="e7019-108">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="e7019-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Eksenler kök düğüme göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="e7019-109">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="e7019-110">Bu ilk örnek kullanarak bir XML ağacı yükler <xref:System.Xml.Linq.XElement.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="e7019-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="e7019-111">Daha sonra ağacın kök öğelerinin alt öğelerini sorgular.</span><span class="sxs-lookup"><span data-stu-id="e7019-111">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="e7019-112">Beklendiği gibi, bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e7019-112">As expected, this example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="e7019-113">Aşağıdaki örnek, XML ağacının bir yerine bir olarak yüklendiği özel durum ile, yukarıdaki bir ile aynıdır <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="e7019-113">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="e7019-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e7019-114">This example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="e7019-115">Aynı sorgunun `Root` üç alt düğüm yerine bir düğümü döndürtiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e7019-115">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="e7019-116">Bu ile ilgilenmeye yönelik bir yaklaşım <xref:System.Xml.Linq.XDocument.Root%2A> , aşağıdaki gibi, eksen yöntemlerine erişmeden önce özelliğini kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="e7019-116">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="e7019-117">Bu sorgu artık, içinde kök ağaçtaki sorgu ile aynı şekilde gerçekleştirilir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="e7019-117">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e7019-118">Örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e7019-118">The example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  