---
title: Statik olarak derlenen sorgular-LINQ to XML
description: LINQ to XML sorgularının statik olarak derlenerek XMLDocument üzerinden performans avantajı elde etme hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 53dd47247eae8802dcf8187d0e82eb1c8bead9f9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553414"
---
# <a name="statically-compiled-queries-linq-to-xml"></a><span data-ttu-id="aede1-103">Statik olarak derlenen sorgular (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="aede1-103">Statically compiled queries (LINQ to XML)</span></span>

<span data-ttu-id="aede1-104">İle karşılaştırıldığında LINQ to XML en önemli performans avantajlarından biri <xref:System.Xml.XmlDocument> , LINQ to XML içindeki sorguların statik olarak derlenmesi, ancak XPath sorgularının çalışma zamanında yorumlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aede1-104">One of the most important performance advantages of LINQ to XML, as compared to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="aede1-105">Bu özellik LINQ to XML yerleşik olarak bulunur, bu nedenle bundan faydalanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken farkın anlaşılması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="aede1-105">This feature is built into LINQ to XML, so you don't have to perform extra steps to take advantage of it, but it's helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="aede1-106">Bu makalede fark açıklanır.</span><span class="sxs-lookup"><span data-stu-id="aede1-106">This article explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="aede1-107">Statik olarak derlenen sorgular ve XPath karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="aede1-107">Statically compiled queries vs. XPath</span></span>

<span data-ttu-id="aede1-108">Aşağıdaki örnek, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aede1-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span> <span data-ttu-id="aede1-109">Eşdeğer XPath ifadesi `//Address[@Type='Shipping']` .</span><span class="sxs-lookup"><span data-stu-id="aede1-109">The equivalent XPath expression is `//Address[@Type='Shipping']`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="aede1-110">Bu örnekteki sorgu ifadesi derleyici tarafından Yöntem tabanlı sorgu sözdizimine yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="aede1-110">The query expression in this example is rewritten by the compiler to method-based query syntax.</span></span> <span data-ttu-id="aede1-111">Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="aede1-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    po
    .Descendants("Address")
    .Where(el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

 ```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="aede1-112"><xref:System.Linq.Enumerable.Where%2A>Yöntemi bir genişletme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="aede1-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="aede1-113">Daha fazla bilgi için bkz. [uzantı metotları (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="aede1-113">For more information, see [Extension Methods (C# Programming Guide)](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="aede1-114"><xref:System.Linq.Enumerable.Where%2A>Bir genişletme yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:</span><span class="sxs-lookup"><span data-stu-id="aede1-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    System.Linq.Enumerable.Where(
        po.Descendants("Address"),
        el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="aede1-115">Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="aede1-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="aede1-116">Bu, sorguların statik olarak bağlı yöntem çağrılarına etkin bir şekilde derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="aede1-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="aede1-117">Yineleyicilerin ertelenmiş yürütme semantiği ile birlikte, performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="aede1-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="aede1-118">Yineleyicilerin ertelenmiş yürütme semantiği hakkında daha fazla bilgi için bkz. [ertelenmiş yürütme ve yavaş değerlendirme](deferred-execution-lazy-evaluation.md).</span><span class="sxs-lookup"><span data-stu-id="aede1-118">For more information about the deferred execution semantics of iterators, see [Deferred execution and lazy evaluation](deferred-execution-lazy-evaluation.md).</span></span>

> [!NOTE]
> <span data-ttu-id="aede1-119">Bu örnekler, derleyicinin yazabilmesi için kod temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="aede1-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="aede1-120">Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak bu örneklere benzer şekilde performans aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="aede1-120">The actual implementation might differ slightly from these examples, but the performance will be the same as, or similar to, these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="aede1-121">XmlDocument ile XPath ifadeleri yürütme</span><span class="sxs-lookup"><span data-stu-id="aede1-121">Executing XPath expressions with XmlDocument</span></span>

<span data-ttu-id="aede1-122">Aşağıdaki örnek, <xref:System.Xml.XmlDocument> önceki örneklerle aynı sonuçları başarmak için kullanır:</span><span class="sxs-lookup"><span data-stu-id="aede1-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

```csharp
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");
XmlDocument doc = new XmlDocument();
doc.Load(reader);
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");
foreach (XmlNode n in nl)
    Console.WriteLine(n.OuterXml);
reader.Close();
```

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

<span data-ttu-id="aede1-123">Bu sorgu, LINQ to XML kullanan örneklerle aynı çıktıyı döndürür; Tek fark, LINQ to XML yazdırılan XML 'nin bu şekilde <xref:System.Xml.XmlDocument> girintilemez.</span><span class="sxs-lookup"><span data-stu-id="aede1-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> doesn't.</span></span>

<span data-ttu-id="aede1-124">Ancak, <xref:System.Xml.XmlDocument> yaklaşım genellikle LINQ to XML, ve <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi her çağrıldığında aşağıdaki işlemleri yapması gerektiğinden, her zaman bir yaklaşım gerçekleştirmez:</span><span class="sxs-lookup"><span data-stu-id="aede1-124">However, the <xref:System.Xml.XmlDocument> approach generally doesn't perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following every time it's called:</span></span>

- <span data-ttu-id="aede1-125">XPath ifadesini içeren dizeyi ayrıştırarak dizeyi belirteçlere bölmek.</span><span class="sxs-lookup"><span data-stu-id="aede1-125">Parse the string that contains the XPath expression, breaking the string into tokens.</span></span>
- <span data-ttu-id="aede1-126">XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="aede1-126">Validate the tokens to make sure that the XPath expression is valid.</span></span>
- <span data-ttu-id="aede1-127">İfadeyi bir iç ifade ağacına çevirin.</span><span class="sxs-lookup"><span data-stu-id="aede1-127">Translate the expression into an internal expression tree.</span></span>
- <span data-ttu-id="aede1-128">İfadenin değerlendirmesine bağlı olarak, sonuç kümesi düğümlerini uygun şekilde seçerek düğümleri üzerinde yineleyin.</span><span class="sxs-lookup"><span data-stu-id="aede1-128">Iterate through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="aede1-129">Bu, karşılık gelen LINQ to XML sorgusu tarafından gerçekleştirilen işin önemli ölçüde daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="aede1-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="aede1-130">Belirli performans farkı farklı sorgu türleri için farklılık gösterir, ancak genel LINQ to XML sorgularında daha az iş olur ve bu nedenle, kullanarak XPath ifadelerini değerlendirmeden daha iyi gerçekleştirilir <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="aede1-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>
