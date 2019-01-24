---
title: Sorgular (LINQ to XML)'statik olarak derlenmiş (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 842f8c1c2fa07e1658992e94e5163222f38f80ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514796"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="9e1b3-102">Sorgular (LINQ to XML)'statik olarak derlenmiş (C#)</span><span class="sxs-lookup"><span data-stu-id="9e1b3-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9e1b3-103">En önemli performans birini avantajlar LINQ, XML olarak <xref:System.Xml.XmlDocument>, XPath sorguları çalışma zamanında yorumlanacağını ancak LINQ to XML sorgularında statik olduğunu, derlenir.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="9e1b3-104">Bu özellik için LINQ to XML, yararlanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknolojiyi arasında seçim yaparken, aradaki farkı kavramak yararlıdır yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="9e1b3-105">Bu konu, farkı açıklar.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="9e1b3-106">Statik olarak derlenmiş sorgular vs. XPath</span><span class="sxs-lookup"><span data-stu-id="9e1b3-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="9e1b3-107">Aşağıdaki örnek belirtilen ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğeleri almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="9e1b3-108">Eşdeğer XPath ifadesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e1b3-108">The following is the equivalent XPath expression:</span></span>  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="9e1b3-109">Bu örnekte sorgu ifadesi metot tabanlı sorgu söz dizimi için derleyici tarafından yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="9e1b3-110">Metot tabanlı sorgu söz dizimi içinde yazılır, aşağıdaki örnekte, önceki'dekiyle aynı sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="9e1b3-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="9e1b3-111"><xref:System.Linq.Enumerable.Where%2A> Bir genişletme yöntemi bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="9e1b3-112">Daha fazla bilgi için [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9e1b3-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="9e1b3-113">Çünkü <xref:System.Linq.Enumerable.Where%2A> bir uzantı yöntemi, yukarıdaki sorgunun yazılmış gibi sorgulamanıza şu şekilde derlenir:</span><span class="sxs-lookup"><span data-stu-id="9e1b3-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="9e1b3-114">Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="9e1b3-115">Bu sorgular, statik olarak bağlı yöntemi çağrılarını etkili bir şekilde derlenir olgu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="9e1b3-116">Bu, yineleyiciler, ertelenmiş yürütme semantikleri ile birleştirilmiş performansını artırır.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="9e1b3-117">Yineleyiciler ertelenmiş yürütme semantikleri hakkında daha fazla bilgi için bkz. [ertelenmiş yürütme ve geç değerlendirme LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9e1b3-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e1b3-118">Bu örnekler derleyici yazabilirsiniz kodun temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="9e1b3-119">Gerçek uygulamalar bu örneklerden biraz farklı olabilir, ancak performans aynı olacaktır ya da bu örneklerde benzer.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="9e1b3-120">XPath ifadeleri XmlDocument ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9e1b3-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="9e1b3-121">Aşağıdaki örnekte <xref:System.Xml.XmlDocument> önceki örnekler aynı sonuçlara ulaşmak için:</span><span class="sxs-lookup"><span data-stu-id="9e1b3-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="9e1b3-122">Bu sorgu, LINQ to XML kullanan örnekler aynı çıkışı döndürür; tek fark LINQ to XML yazdırılan XML girintiler takvimidir <xref:System.Xml.XmlDocument> desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="9e1b3-123">Ancak, <xref:System.Xml.XmlDocument> yaklaşımı genellikle gerçekleştirmez LINQ to XML, yanı sıra çünkü <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi aşağıdakileri yapmalıdır dahili olarak her çağrıldığında:</span><span class="sxs-lookup"><span data-stu-id="9e1b3-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="9e1b3-124">Bu dizeyi belirteçlere bozucu bir XPath ifadesi içeriyor dizeyi ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="9e1b3-125">Bu XPath ifadesi geçerli olduğundan emin olmak için belirteçlerini doğrular.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="9e1b3-126">Bu iç ifade ağacı ifadeye çevrilir.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="9e1b3-127">Uygun şekilde ifade değerlendirmeye göre sonuç kümesi için düğümleri seçme düğümleri aracılığıyla yinelenir.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="9e1b3-128">Önemli ölçüde daha fazla ilgili LINQ to XML sorgusu ile çalışmanın budur.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="9e1b3-129">Sorgu farklı türleri için belirli bir performans farkı değişir, ancak genel bir LINQ to XML sorguları daha az çalışma yapın ve bu nedenle, daha iyi kullanarak XPath ifadelerini değerlendirme gerçekleştirmek <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e1b3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e1b3-130">See also</span></span>

- [<span data-ttu-id="9e1b3-131">Performans (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9e1b3-131">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
