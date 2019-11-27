---
title: Statik Olarak Derlenmiş Sorgular (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: e9f56366f1566f831f1e0ea5bd5a06775d698c3d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350575"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="d8183-102">Statik olarak derlenen sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8183-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="d8183-103"><xref:System.Xml.XmlDocument>aksine LINQ to XML en önemli performans avantajlarından biri, LINQ to XML sorguların statik olarak derlenmesine karşın XPath sorgularının çalışma zamanında yorumlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8183-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="d8183-104">Bu özellik LINQ to XML ' de yerleşiktir. bu nedenle, bundan faydalanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken farkın anlaşılması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="d8183-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="d8183-105">Bu konu, farkı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8183-105">This topic explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="d8183-106">Statik olarak derlenen sorgular ve XPath karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="d8183-106">Statically Compiled Queries vs. XPath</span></span>

<span data-ttu-id="d8183-107">Aşağıdaki örnek, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8183-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>

<span data-ttu-id="d8183-108">Eşdeğer XPath ifadesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d8183-108">The following is the equivalent XPath expression:</span></span>

```vb
//Address[@Type='Shipping']
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="d8183-109">Bu örnekteki sorgu ifadesi derleyici tarafından Yöntem tabanlı sorgu söz dizimine yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="d8183-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="d8183-110">Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="d8183-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="d8183-111"><xref:System.Linq.Enumerable.Where%2A> yöntemi bir genişletme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="d8183-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="d8183-112">Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d8183-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="d8183-113"><xref:System.Linq.Enumerable.Where%2A> bir genişletme yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:</span><span class="sxs-lookup"><span data-stu-id="d8183-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="d8183-114">Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="d8183-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="d8183-115">Bu, sorguların statik olarak bağlı yöntem çağrılarına etkin bir şekilde derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8183-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="d8183-116">Yineleyicilerin ertelenmiş yürütme semantiği ile birlikte, performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="d8183-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="d8183-117">Yineleyicilerin ertelenmiş yürütme semantiği hakkında daha fazla bilgi için bkz. [LINQ to XML ertelenmiş yürütme ve geç değerlendirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d8183-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d8183-118">Bu örnekler, derleyicinin yazabilmesi için kod temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="d8183-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="d8183-119">Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak performans aynı veya bu örneklere benzer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d8183-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="d8183-120">XmlDocument ile XPath Ifadeleri yürütme</span><span class="sxs-lookup"><span data-stu-id="d8183-120">Executing XPath Expressions with XmlDocument</span></span>

<span data-ttu-id="d8183-121">Aşağıdaki örnek, önceki örneklerle aynı sonuçları başarmak için <xref:System.Xml.XmlDocument> kullanır:</span><span class="sxs-lookup"><span data-stu-id="d8183-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

<span data-ttu-id="d8183-122">Bu sorgu, LINQ to XML kullanan örneklerle aynı çıktıyı döndürür; Tek fark, LINQ to XML yazdırılan XML 'nin girintilebilirken <xref:System.Xml.XmlDocument> değildir.</span><span class="sxs-lookup"><span data-stu-id="d8183-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>

<span data-ttu-id="d8183-123">Ancak, <xref:System.Xml.XmlDocument> yaklaşımı genellikle LINQ to XML ve <xref:System.Xml.XmlNode.SelectNodes%2A> yönteminin her çağrılışında aşağıdakileri yapması gerektiğinden, her zaman bir şekilde gerçekleştirmez:</span><span class="sxs-lookup"><span data-stu-id="d8183-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>

- <span data-ttu-id="d8183-124">XPath ifadesini içeren dizeyi ayrıştırır ve dizeyi belirteçlere ayırır.</span><span class="sxs-lookup"><span data-stu-id="d8183-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>

- <span data-ttu-id="d8183-125">XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="d8183-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>

- <span data-ttu-id="d8183-126">İfadeyi bir iç ifade ağacına çevirir.</span><span class="sxs-lookup"><span data-stu-id="d8183-126">It translates the expression into an internal expression tree.</span></span>

- <span data-ttu-id="d8183-127">İfadenin değerlendirmesine bağlı olarak sonuç kümesi düğümlerini uygun şekilde seçerek düğümleri üzerinde dolaşır.</span><span class="sxs-lookup"><span data-stu-id="d8183-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="d8183-128">Bu, karşılık gelen LINQ to XML sorgusu tarafından gerçekleştirilen işin önemli ölçüde daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="d8183-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="d8183-129">Belirli performans farkı farklı sorgu türleri için farklılık gösterir, ancak genel LINQ to XML sorgularında daha az iş yapılır ve bu nedenle, <xref:System.Xml.XmlDocument>kullanarak XPath ifadelerini değerlendirmeden daha iyi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d8183-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8183-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8183-130">See also</span></span>

- [<span data-ttu-id="d8183-131">Performans (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8183-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
