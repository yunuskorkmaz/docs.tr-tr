---
title: Statik Olarak Derlenen Sorgular (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253024"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="d2669-102">Statik Olarak Derlenen Sorgular (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2669-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d2669-103">Linq'in XML'e en önemli performans <xref:System.Xml.XmlDocument>avantajlarından biri, Linq'ten XML'e sorguların statik olarak derlenmiş olması, XPath sorgularının ise çalışma zamanında yorumlanması gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="d2669-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="d2669-104">Bu özellik LINQ'dan XML'e kadar yerleşiktir, bu nedenle bundan yararlanmak için ekstra adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken ayrımı anlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d2669-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="d2669-105">Bu konu farkı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d2669-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="d2669-106">Statik Olarak Derlenen Sorgular vs XPath</span><span class="sxs-lookup"><span data-stu-id="d2669-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="d2669-107">Aşağıdaki örnek, belirli bir ada sahip ve belirtilen değere sahip bir öznitelik ile soyundan gelen öğeleri nasıl elde etmek için gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2669-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="d2669-108">Aşağıda eşdeğer XPath ifadesi veremistir:`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="d2669-108">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d2669-109">Bu örnekteki sorgu ifadesi derleyici tarafından yöntem tabanlı sorgu sözdizimine yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="d2669-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="d2669-110">Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="d2669-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d2669-111">Yöntem <xref:System.Linq.Enumerable.Where%2A> bir uzantı yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="d2669-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="d2669-112">Daha fazla bilgi için [Uzantı Yöntemleri'ne](../../classes-and-structs/extension-methods.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d2669-112">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="d2669-113">Bir <xref:System.Linq.Enumerable.Where%2A> uzantı yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:</span><span class="sxs-lookup"><span data-stu-id="d2669-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d2669-114">Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="d2669-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="d2669-115">Bu, sorguların statik olarak bağlı yöntem çağrılarına etkili bir şekilde derlenmiş olduğu gerçeğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2669-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="d2669-116">Bu, yineleyicilerin ertelenmiş yürütme semantiği ile birlikte performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="d2669-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="d2669-117">Yineleyicilerin ertelenmiş yürütme semantikleri hakkında daha fazla bilgi için [LINQ'da XML'e (C#) Ertelenmiş Yürütme ve Tembel Değerlendirme bölümüne](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d2669-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2669-118">Bu örnekler, derleyicinin yazabileceği kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d2669-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="d2669-119">Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak performans bu örneklerle aynı veya benzer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d2669-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="d2669-120">XmlDocument ile XPath İfadelerini Yürütme</span><span class="sxs-lookup"><span data-stu-id="d2669-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="d2669-121">Aşağıdaki örnek, <xref:System.Xml.XmlDocument> önceki örneklerle aynı sonuçları gerçekleştirmek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="d2669-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="d2669-122">Bu sorgu, LINQ'u XML'e kullanan örneklerle aynı çıktıyı döndürür; tek fark, LinQ xml için yazılı XML girintisi, oysa <xref:System.Xml.XmlDocument> yok.</span><span class="sxs-lookup"><span data-stu-id="d2669-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="d2669-123">Ancak, <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlNode.SelectNodes%2A> yöntem her çağrıldığında dahili olarak aşağıdakileri yapmak gerekir, çünkü yaklaşım genellikle XML için LINQ gibi performans göstermez:</span><span class="sxs-lookup"><span data-stu-id="d2669-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="d2669-124">XPath ifadesini içeren dizeyi ayrışturarak dizeyi belirteçlere ayırır.</span><span class="sxs-lookup"><span data-stu-id="d2669-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="d2669-125">XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="d2669-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="d2669-126">İfadeyi bir iç ifade ağacına çevirir.</span><span class="sxs-lookup"><span data-stu-id="d2669-126">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="d2669-127">İfadenin değerlendirilmesi temel alınarak sonuç kümesi için düğümleri uygun bir şekilde seçerek düğümleri yineler.</span><span class="sxs-lookup"><span data-stu-id="d2669-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="d2669-128">Bu, ilgili LINQ ile XML sorgusu nun yaptığı işten önemli ölçüde daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="d2669-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="d2669-129">Belirli performans farkı farklı sorgu türlerine göre değişir, ancak genel olarak LinQ'dan XML sorgularına daha az iş <xref:System.Xml.XmlDocument>yapar ve bu nedenle XPath ifadelerini kullanarak değerlendirmekten daha iyi performans gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2669-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
