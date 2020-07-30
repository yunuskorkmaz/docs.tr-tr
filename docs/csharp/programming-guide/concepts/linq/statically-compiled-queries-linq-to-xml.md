---
title: Statik olarak derlenen sorgular (LINQ to XML) (C#)
description: C# ' de LINQ to XML statik olarak derlenen sorgular ve bunların, çalışma zamanında yorumlanması gereken XPath sorgularından farklı oldukları hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: cd2e6a6507311d5fc17215a22c70bd0449292b6f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302314"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="c0929-103">Statik olarak derlenen sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c0929-103">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c0929-104">En önemli performans avantajlarından biri de LINQ to XML, <xref:System.Xml.XmlDocument> LINQ to XML içindeki sorguların statik olarak derlenmesine karşın XPath sorgularının çalışma zamanında yorumlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0929-104">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="c0929-105">Bu özellik LINQ to XML ' de yerleşiktir. bu nedenle, bundan faydalanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken farkın anlaşılması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="c0929-105">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="c0929-106">Bu konu, farkı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0929-106">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="c0929-107">Statik olarak derlenen sorgular ve XPath karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="c0929-107">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="c0929-108">Aşağıdaki örnek, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0929-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="c0929-109">Eşdeğer XPath ifadesi aşağıda verilmiştir:`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="c0929-109">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="c0929-110">Bu örnekteki sorgu ifadesi derleyici tarafından Yöntem tabanlı sorgu söz dizimine yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="c0929-110">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="c0929-111">Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="c0929-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="c0929-112"><xref:System.Linq.Enumerable.Where%2A>Yöntemi bir genişletme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="c0929-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="c0929-113">Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c0929-113">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="c0929-114"><xref:System.Linq.Enumerable.Where%2A>Bir genişletme yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:</span><span class="sxs-lookup"><span data-stu-id="c0929-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="c0929-115">Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="c0929-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="c0929-116">Bu, sorguların statik olarak bağlı yöntem çağrılarına etkin bir şekilde derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0929-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="c0929-117">Yineleyicilerin ertelenmiş yürütme semantiği ile birlikte, performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="c0929-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="c0929-118">Yineleyicilerin ertelenmiş yürütme semantiği hakkında daha fazla bilgi için bkz. [LINQ to XML (C#) Içinde ertelenmiş yürütme ve yavaş değerlendirme](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c0929-118">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0929-119">Bu örnekler, derleyicinin yazabilmesi için kod temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="c0929-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="c0929-120">Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak performans aynı veya bu örneklere benzer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c0929-120">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="c0929-121">XmlDocument ile XPath Ifadeleri yürütme</span><span class="sxs-lookup"><span data-stu-id="c0929-121">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="c0929-122">Aşağıdaki örnek, <xref:System.Xml.XmlDocument> önceki örneklerle aynı sonuçları başarmak için kullanır:</span><span class="sxs-lookup"><span data-stu-id="c0929-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="c0929-123">Bu sorgu, LINQ to XML kullanan örneklerle aynı çıktıyı döndürür; Tek fark, LINQ to XML yazdırılan XML 'nin girintilebilirken, bunun farklılığı değildir <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="c0929-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="c0929-124">Ancak, <xref:System.Xml.XmlDocument> yaklaşım genellikle LINQ to XML, ve yöntemi her çağrıldığında aşağıdaki işlemleri yapması gerektiğinden, <xref:System.Xml.XmlNode.SelectNodes%2A> her zaman yaklaşım uygulanmaz:</span><span class="sxs-lookup"><span data-stu-id="c0929-124">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="c0929-125">XPath ifadesini içeren dizeyi ayrıştırır ve dizeyi belirteçlere ayırır.</span><span class="sxs-lookup"><span data-stu-id="c0929-125">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="c0929-126">XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="c0929-126">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="c0929-127">İfadeyi bir iç ifade ağacına çevirir.</span><span class="sxs-lookup"><span data-stu-id="c0929-127">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="c0929-128">İfadenin değerlendirmesine bağlı olarak sonuç kümesi düğümlerini uygun şekilde seçerek düğümleri üzerinde dolaşır.</span><span class="sxs-lookup"><span data-stu-id="c0929-128">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="c0929-129">Bu, karşılık gelen LINQ to XML sorgusu tarafından gerçekleştirilen işin önemli ölçüde daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="c0929-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="c0929-130">Belirli performans farkı farklı sorgu türleri için farklılık gösterir, ancak genel LINQ to XML sorgularında daha az iş olur ve bu nedenle, kullanarak XPath ifadelerini değerlendirmeden daha iyi gerçekleştirilir <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="c0929-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
