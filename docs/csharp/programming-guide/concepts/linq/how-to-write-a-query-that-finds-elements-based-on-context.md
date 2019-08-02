---
title: 'Nasıl yapılır: Bağlam (C#) temelinde öğeleri bulan bir sorgu yazın'
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: f6fd0a9dc0f2579185f2f72997f1d406a885c636
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710033"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="e5e71-102">Nasıl yapılır: Bağlam (C#) temelinde öğeleri bulan bir sorgu yazın</span><span class="sxs-lookup"><span data-stu-id="e5e71-102">How to: Write a Query that Finds Elements Based on Context (C#)</span></span>
<span data-ttu-id="e5e71-103">Bazen, bağlamlarına göre öğeleri seçen bir sorgu yazmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e5e71-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="e5e71-104">Önceki veya sonraki eşdüzey öğelere göre filtrelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5e71-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="e5e71-105">Alt veya üst öğe öğelerine göre filtrelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5e71-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="e5e71-106">Bunu, `where` bir sorgu yazarak ve yan tümcesindeki sorgunun sonuçlarını kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5e71-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="e5e71-107">İlk olarak null ile test etmeniz ve sonra değeri test etmeniz gerekiyorsa, bir `let` yan tümce içinde sorgu yapmak daha uygundur ve sonra sonuçları `where` yan tümce içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5e71-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5e71-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5e71-108">Example</span></span>  
 <span data-ttu-id="e5e71-109">Aşağıdaki örnek, hemen arkasından `p` bir `ul` öğesi olan tüm öğeleri seçer.</span><span class="sxs-lookup"><span data-stu-id="e5e71-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="e5e71-110">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e5e71-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="e5e71-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5e71-111">Example</span></span>  
 <span data-ttu-id="e5e71-112">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5e71-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e5e71-113">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e5e71-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="e5e71-114">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e5e71-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5e71-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5e71-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
