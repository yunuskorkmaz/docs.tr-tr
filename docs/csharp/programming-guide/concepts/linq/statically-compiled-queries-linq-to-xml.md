---
title: Statik olarak derlenen sorgular (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: db9cec3282e9f531471c2a5908ddbf2acef90ca6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590983"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="625ff-102">Statik olarak derlenen sorgular (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="625ff-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="625ff-103">En önemli performans avantajlarından biri de LINQ to XML <xref:System.Xml.XmlDocument>, LINQ to XML içindeki sorguların statik olarak derlenmesine karşın XPath sorgularının çalışma zamanında yorumlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="625ff-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="625ff-104">Bu özellik LINQ to XML ' de yerleşiktir. bu nedenle, bundan faydalanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken farkın anlaşılması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="625ff-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="625ff-105">Bu konu, farkı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="625ff-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="625ff-106">Statik olarak derlenen sorgular ve XPath</span><span class="sxs-lookup"><span data-stu-id="625ff-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="625ff-107">Aşağıdaki örnek, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="625ff-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="625ff-108">Eşdeğer XPath ifadesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="625ff-108">The following is the equivalent XPath expression:</span></span>  
  
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
  
 <span data-ttu-id="625ff-109">Bu örnekteki sorgu ifadesi derleyici tarafından Yöntem tabanlı sorgu söz dizimine yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="625ff-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="625ff-110">Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="625ff-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="625ff-111"><xref:System.Linq.Enumerable.Where%2A> Yöntemi bir genişletme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="625ff-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="625ff-112">Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="625ff-112">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="625ff-113">Bir <xref:System.Linq.Enumerable.Where%2A> genişletme yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:</span><span class="sxs-lookup"><span data-stu-id="625ff-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="625ff-114">Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="625ff-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="625ff-115">Bu, sorguların statik olarak bağlı yöntem çağrılarına etkin bir şekilde derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="625ff-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="625ff-116">Yineleyicilerin ertelenmiş yürütme semantiği ile birlikte, performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="625ff-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="625ff-117">Yineleyicilerin ertelenmiş yürütme semantiği hakkında daha fazla bilgi için bkz. [LINQ to XMLC#() içinde ertelenmiş yürütme ve geç değerlendirme](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="625ff-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="625ff-118">Bu örnekler, derleyicinin yazabilmesi için kod temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="625ff-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="625ff-119">Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak performans aynı veya bu örneklere benzer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="625ff-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="625ff-120">XmlDocument ile XPath Ifadeleri yürütme</span><span class="sxs-lookup"><span data-stu-id="625ff-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="625ff-121">Aşağıdaki örnek, önceki <xref:System.Xml.XmlDocument> örneklerle aynı sonuçları başarmak için kullanır:</span><span class="sxs-lookup"><span data-stu-id="625ff-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="625ff-122">Bu sorgu, LINQ to XML kullanan örneklerle aynı çıktıyı döndürür; Tek fark, LINQ to XML yazdırılan XML 'nin girintilebilirken <xref:System.Xml.XmlDocument> , bunun farklılığı değildir.</span><span class="sxs-lookup"><span data-stu-id="625ff-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="625ff-123">Ancak, <xref:System.Xml.XmlNode.SelectNodes%2A> yaklaşım genellikle LINQ to XML, ve yöntemi her çağrıldığında aşağıdaki işlemleri yapması gerektiğinden, her zaman yaklaşım uygulanmaz: <xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="625ff-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="625ff-124">XPath ifadesini içeren dizeyi ayrıştırır ve dizeyi belirteçlere ayırır.</span><span class="sxs-lookup"><span data-stu-id="625ff-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="625ff-125">XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="625ff-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="625ff-126">İfadeyi bir iç ifade ağacına çevirir.</span><span class="sxs-lookup"><span data-stu-id="625ff-126">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="625ff-127">İfadenin değerlendirmesine bağlı olarak sonuç kümesi düğümlerini uygun şekilde seçerek düğümleri üzerinde dolaşır.</span><span class="sxs-lookup"><span data-stu-id="625ff-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="625ff-128">Bu, karşılık gelen LINQ to XML sorgusu tarafından gerçekleştirilen işin önemli ölçüde daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="625ff-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="625ff-129">Belirli performans farkı farklı sorgu türleri için farklılık gösterir, ancak genel LINQ to XML sorgularında daha az iş olur ve bu nedenle, kullanarak <xref:System.Xml.XmlDocument>XPath ifadelerini değerlendirmeden daha iyi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="625ff-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  