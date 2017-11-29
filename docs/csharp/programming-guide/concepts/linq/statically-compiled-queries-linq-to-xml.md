---
title: "Sorgu (LINQ-XML)'statik olarak derlenmiş (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 15ba867951ca4df1d203b837318ca2cc9eb91e7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="7c73b-102">Sorgu (LINQ-XML)'statik olarak derlenmiş (C#)</span><span class="sxs-lookup"><span data-stu-id="7c73b-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7c73b-103">En önemli performans birini avantaj LINQ XML'e tersine <xref:System.Xml.XmlDocument>, çalışma zamanında XPath sorguları yorumlanacağını ancak LINQ-XML sorgularında statik olduğundan, derlenir.</span><span class="sxs-lookup"><span data-stu-id="7c73b-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="7c73b-104">Bu özellik LINQ-XML, onu yararlanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknolojiyi arasında seçerken aralarındaki farkı anlamak faydalıdır şekilde de yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="7c73b-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="7c73b-105">Bu konuda fark açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c73b-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="7c73b-106">Statik olarak derlenmiş sorguları vs. XPath</span><span class="sxs-lookup"><span data-stu-id="7c73b-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="7c73b-107">Aşağıdaki örnek belirtilen ada sahip ve belirtilen değerli özniteliği içeren alt öğelerini alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7c73b-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="7c73b-108">Eşdeğer XPath ifadesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7c73b-108">The following is the equivalent XPath expression:</span></span>  
  
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
  
 <span data-ttu-id="7c73b-109">Bu örnek sorgu ifadesinde yöntem temelli sorgu söz dizimi derleyicisi tarafından yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="7c73b-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="7c73b-110">Yöntem temelli sorgu söz dizimi yazılır, aşağıdaki örnek öncekiyle aynı sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="7c73b-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="7c73b-111"><xref:System.Linq.Enumerable.Where%2A> Bir genişletme yöntemi bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="7c73b-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="7c73b-112">Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7c73b-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="7c73b-113">Çünkü <xref:System.Linq.Enumerable.Where%2A> bir uzantı yöntemidir yazılmış gibi sorgulamanıza gibi yukarıdaki sorgu derlenir:</span><span class="sxs-lookup"><span data-stu-id="7c73b-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="7c73b-114">Bu örnek, önceki iki örnek ile tam olarak aynı sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="7c73b-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="7c73b-115">Bu sorguları statik olarak bağlantılı yöntemi çağrılarını etkili bir şekilde derlenen olgu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7c73b-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="7c73b-116">Bu, birleştirilmiş yineleyiciler, ertelenmiş yürütme semantiği ile performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="7c73b-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="7c73b-117">Yineleyiciler ertelenmiş yürütme semantiğini hakkında daha fazla bilgi için bkz: [ertelenmiş yürütme ve LINQ-XML (C#) geç değerlendirme](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7c73b-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c73b-118">Bu örnekler derleyici yazabilir kod temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="7c73b-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="7c73b-119">Gerçek uygulamayı bu örneklerinden biraz farklı olabilir, ancak performans aynı olacaktır ya da bu örneklerde benzer.</span><span class="sxs-lookup"><span data-stu-id="7c73b-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="7c73b-120">XPath ifadeleri XmlDocument ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7c73b-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="7c73b-121">Aşağıdaki örnek kullanır <xref:System.Xml.XmlDocument> önceki örneklerle aynı sonuçları gerçekleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="7c73b-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="7c73b-122">Bu sorgu LINQ-XML kullanma örnekleri aynı çıktıyı döndürür; yalnızca LINQ-XML yazdırılan XML girintileri ancak farktır <xref:System.Xml.XmlDocument> desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7c73b-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="7c73b-123">Ancak, <xref:System.Xml.XmlDocument> yaklaşım genellikle gerçekleştirmez LINQ-XML, yanı sıra çünkü <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi aşağıdakileri yapmalıdır dahili olarak her çağrıldığında:</span><span class="sxs-lookup"><span data-stu-id="7c73b-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="7c73b-124">Dizeyi belirteçlere çiğnemekten XPath ifadesi içeren dizeyi ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="7c73b-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="7c73b-125">XPath ifadesi geçerli olduğundan emin olmak için belirteçlerini doğrular.</span><span class="sxs-lookup"><span data-stu-id="7c73b-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="7c73b-126">Bir iç ifade ağacına ifadesine çevirir.</span><span class="sxs-lookup"><span data-stu-id="7c73b-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="7c73b-127">Uygun şekilde ifade değerlendirmeye dayanarak sonuç kümesi için düğüm seçildikten düğümleri dolaşır.</span><span class="sxs-lookup"><span data-stu-id="7c73b-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="7c73b-128">Önemli ölçüde daha fazla XML sorgusu için karşılık gelen LINQ tarafından çalışmanın budur.</span><span class="sxs-lookup"><span data-stu-id="7c73b-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="7c73b-129">Sorgu farklı türleri için belirli bir performans farkı değişir, ancak genel LINQ-XML sorguları daha az çalışma yapın ve bu nedenle, daha iyi kullanarak XPath ifadeleri değerlendirme görevlerini <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="7c73b-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c73b-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c73b-130">See Also</span></span>  
 [<span data-ttu-id="7c73b-131">Performans (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c73b-131">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
