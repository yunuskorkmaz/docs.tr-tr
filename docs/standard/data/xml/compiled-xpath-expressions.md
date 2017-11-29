---
title: "Derlenmiş XPath ifadeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f7b812d5d6f75e39e9eebcc003686ff88d009e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="93a37-102">Derlenmiş XPath ifadeleri</span><span class="sxs-lookup"><span data-stu-id="93a37-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="93a37-103">Bir <xref:System.Xml.XPath.XPathExpression> nesneyi temsil ediyor herhangi birinden statik döndürülen derlenmiş bir XPath sorgusu <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> sınıfı veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="93a37-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="93a37-104">XPathExpression sınıfı</span><span class="sxs-lookup"><span data-stu-id="93a37-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="93a37-105">Bir XPath sorgusu tarafından temsil edilen derlenmiş bir <xref:System.Xml.XPath.XPathExpression> nesnesidir aynı XPath sorgusu birden çok kez kullanılıyorsa yararlı.</span><span class="sxs-lookup"><span data-stu-id="93a37-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="93a37-106">Örneğin, çağrılırken <xref:System.Xml.XPath.XPathNavigator.Select%2A> XPath sorgusu her zaman temsil eden bir dize kullanmak yerine, birden çok kez yöntemi kullanın <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> sınıfı veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> derlemek için sınıf ve XPath sorgusunda önbelleğe bir <xref:System.Xml.XPath.XPathExpression> yeniden ve performansı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="93a37-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="93a37-107">Bir kez derlenmiş <xref:System.Xml.XPath.XPathExpression> nesnesi, aşağıdaki girdi olarak kullanılabilecek <xref:System.Xml.XPath.XPathNavigator> türüne bağlı olarak sınıfı yöntemleri XPath sorgudan döndürülen.</span><span class="sxs-lookup"><span data-stu-id="93a37-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="93a37-108">Aşağıdaki tabloda her W3C XPath dönüş türleri, kendi Microsoft .NET Framework Eşitlikleri ve ne açıklanmaktadır yöntemleri <xref:System.Xml.XPath.XPathExpression> nesnesi kullanılabilir ile dönüş türüne göre.</span><span class="sxs-lookup"><span data-stu-id="93a37-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="93a37-109">W3C XPath dönüş türü</span><span class="sxs-lookup"><span data-stu-id="93a37-109">W3C XPath Return Type</span></span>|<span data-ttu-id="93a37-110">.NET framework eşdeğeri türü</span><span class="sxs-lookup"><span data-stu-id="93a37-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="93a37-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93a37-111">Description</span></span>|<span data-ttu-id="93a37-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="93a37-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="93a37-113">Belge sırada oluşturulan çoğaltmaları olmadan düğümler sırasız bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="93a37-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="93a37-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A>veya<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="93a37-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="93a37-115">A `true` veya `false` değeri.</span><span class="sxs-lookup"><span data-stu-id="93a37-115">A `true` or `false` value.</span></span>|<span data-ttu-id="93a37-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>veya</span><span class="sxs-lookup"><span data-stu-id="93a37-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="93a37-117">Bir kayan noktalı sayı.</span><span class="sxs-lookup"><span data-stu-id="93a37-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="93a37-118">UCS bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="93a37-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <span data-ttu-id="93a37-119"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi bir XPath ifadesi, parametre olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="93a37-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="93a37-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Yöntemi döndürür bir <xref:System.Xml.XPath.XPathNavigator> nesnesi, W3C XPath dönüş türleri birini değil.</span><span class="sxs-lookup"><span data-stu-id="93a37-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="93a37-121">ReturnType özelliği</span><span class="sxs-lookup"><span data-stu-id="93a37-121">The ReturnType Property</span></span>  
 <span data-ttu-id="93a37-122">İçine sorgu derlendikten sonra XPath bir <xref:System.Xml.XPath.XPathExpression> nesne kullanabileceğiniz <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> özelliği <xref:System.Xml.XPath.XPathExpression> ne XPath sorgusu döndürür belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="93a37-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="93a37-123"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Özelliği aşağıdakilerden birini döndürür <xref:System.Xml.XPath.XPathResultType> W3C XPath temsil eden numaralandırma değerlerinden dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="93a37-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="93a37-124">Aşağıdaki örnek kullanır <xref:System.Xml.XPath.XPathExpression> bir sayı ve kümeden bir düğümü döndürmek için nesne `books.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="93a37-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="93a37-125"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Her özellik <xref:System.Xml.XPath.XPathExpression> nesne sonuçlarından yanı sıra <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemleri konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="93a37-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 <span data-ttu-id="93a37-126">Örnek alır `books.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="93a37-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="93a37-127">Daha yüksek performans XPath ifadeleri</span><span class="sxs-lookup"><span data-stu-id="93a37-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="93a37-128">Daha iyi performans için sorgularınızda olası en belirgin XPath ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="93a37-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="93a37-129">Örneğin, varsa `book` düğümdür alt düğümü `bookstore` düğümü ve `bookstore` düğümdür XPath ifadesini kullanarak bir XML belgesi en üstteki öğe `/bookstore/book` kullanmaktan daha hızlıdır `//book`.</span><span class="sxs-lookup"><span data-stu-id="93a37-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="93a37-130">`//book` XPath ifadesi eşleşen düğümleri tanımlamak için XML ağaç kümedeki her düğüm tarama.</span><span class="sxs-lookup"><span data-stu-id="93a37-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="93a37-131">Ayrıca, düğüm tarafından sağlanan gezinti yöntemlerini kümelerini kullanma <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından sağlanan seçim yöntemlerini üzerinden geliştirilmiş performans sonuçlanabilir <xref:System.Xml.XPath.XPathNavigator> seçim kriterleri nerede basit durumlarda sınıfı.</span><span class="sxs-lookup"><span data-stu-id="93a37-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="93a37-132">Geçerli düğüm ilk alt öğesini seçmeniz gerekir, örneğin, kullanılacak hızlıdır <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> kullanımı çok yöntemi `child::*[1]` XPath ifadesi ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93a37-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="93a37-133">Düğüm hakkında daha fazla bilgi için gezinti yöntemlerini ayarlayın <xref:System.Xml.XPath.XPathNavigator> sınıfı için bkz: [düğüm kümesi Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="93a37-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a37-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93a37-134">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="93a37-135">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="93a37-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="93a37-136">XML verileri XPathNavigator kullanarak seçin</span><span class="sxs-lookup"><span data-stu-id="93a37-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="93a37-137">XPath XPathNavigator kullanarak ifadeler değerlendir</span><span class="sxs-lookup"><span data-stu-id="93a37-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="93a37-138">Eşleşen düğümleri XPathNavigator kullanma</span><span class="sxs-lookup"><span data-stu-id="93a37-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="93a37-139">XPath sorguları tanınan düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="93a37-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="93a37-140">XPath sorguları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="93a37-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
