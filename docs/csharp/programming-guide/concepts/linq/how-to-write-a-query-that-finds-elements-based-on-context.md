---
title: "Nasıl yapılır: bağlama göre (C#) öğeleri bulur bir sorgu yazın"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a9e818c5e0967a6d146cd48b81aebcba4bbdde3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="f5d03-102">Nasıl yapılır: bağlama göre (C#) öğeleri bulur bir sorgu yazın</span><span class="sxs-lookup"><span data-stu-id="f5d03-102">How to: Write a Query that Finds Elements Based on Context (C#)</span></span>
<span data-ttu-id="f5d03-103">Bazen kendi bağlamına dayalı öğeleri seçer bir sorgu yazmak zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d03-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="f5d03-104">Temel alınarak önceki veya Eşdüzey öğeleri aşağıdaki filtre uygulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d03-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="f5d03-105">Temel alınarak alt veya üst öğeleri Filtrele isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d03-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="f5d03-106">Sorgu yazma ve sorgunun sonuçlarını kullanarak bunu yapabilirsiniz `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f5d03-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="f5d03-107">İlk null karşı test etmek ve değeri test etmek varsa, sorgu yapmak daha kullanışlı bir `let` yan tümcesi ve ardından sonuçları `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f5d03-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5d03-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5d03-108">Example</span></span>  
 <span data-ttu-id="f5d03-109">Aşağıdaki örnekte tüm seçer `p` tarafından hemen ardından öğeleri bir `ul` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f5d03-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="f5d03-110">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f5d03-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="f5d03-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5d03-111">Example</span></span>  
 <span data-ttu-id="f5d03-112">Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5d03-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="f5d03-113">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="f5d03-113">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="f5d03-114">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f5d03-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5d03-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5d03-115">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Parse%2A>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
 <xref:System.Linq.Enumerable.FirstOrDefault%2A>  
 [<span data-ttu-id="f5d03-116">Temel sorgu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f5d03-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
