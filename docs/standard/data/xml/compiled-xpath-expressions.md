---
title: Derlenmiş XPath İfadeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1716488f6e072b09469dfbe5cc8fb4965e5db44c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669140"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="d0f52-102">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="d0f52-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="d0f52-103">Bir <xref:System.Xml.XPath.XPathExpression> nesneyi temsil ediyor öğesinden döndürülen statik olarak derlenmiş bir XPath sorgusu <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> sınıfı veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d0f52-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="d0f52-104">XPathExpression sınıfı</span><span class="sxs-lookup"><span data-stu-id="d0f52-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="d0f52-105">Bir XPath sorgusu tarafından temsil edilen derlenmiş bir <xref:System.Xml.XPath.XPathExpression> nesne, aynı XPath sorgusu birden çok kez kullanılıyorsa kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d0f52-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="d0f52-106">Örneğin, çağrılırken <xref:System.Xml.XPath.XPathNavigator.Select%2A> XPath sorgusu her zaman temsil eden bir dize kullanmak yerine, birden çok kez yöntemini kullanın <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> sınıfı veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> derlemek için sınıf ve XPath sorgusundaki önbelleğe bir <xref:System.Xml.XPath.XPathExpression> yeniden kullanımı ve performansı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d0f52-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="d0f52-107">Bir kez derlenmesinin sonra <xref:System.Xml.XPath.XPathExpression> nesne, aşağıdaki giriş olarak kullanılabilir <xref:System.Xml.XPath.XPathNavigator> türüne bağlı olarak sınıfı yöntemleri XPath sorgusundan döndürülen.</span><span class="sxs-lookup"><span data-stu-id="d0f52-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="d0f52-108">Aşağıdaki tablo W3C XPath dönüş türleri, kendi Microsoft .NET Framework Eşitlikleri ve hangi açıklar yöntemleri <xref:System.Xml.XPath.XPathExpression> nesne kullanılabilir olan kendi dönüş türüne göre.</span><span class="sxs-lookup"><span data-stu-id="d0f52-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="d0f52-109">W3C XPath dönüş türü</span><span class="sxs-lookup"><span data-stu-id="d0f52-109">W3C XPath Return Type</span></span>|<span data-ttu-id="d0f52-110">.NET framework eşdeğeri türü</span><span class="sxs-lookup"><span data-stu-id="d0f52-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="d0f52-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0f52-111">Description</span></span>|<span data-ttu-id="d0f52-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d0f52-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="d0f52-113">Belge sırada oluşturulan çoğaltmaları olmadan düğümler sırasız bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d0f52-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="d0f52-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> veya <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="d0f52-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="d0f52-115">A `true` veya `false` değeri.</span><span class="sxs-lookup"><span data-stu-id="d0f52-115">A `true` or `false` value.</span></span>|<span data-ttu-id="d0f52-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> veya</span><span class="sxs-lookup"><span data-stu-id="d0f52-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="d0f52-117">Bir kayan noktalı sayı.</span><span class="sxs-lookup"><span data-stu-id="d0f52-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="d0f52-118">UCS karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="d0f52-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <span data-ttu-id="d0f52-119"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi bir XPath ifadesi, parametre olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d0f52-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="d0f52-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Yöntemi döndürür bir <xref:System.Xml.XPath.XPathNavigator> nesnesi, W3C XPath dönüş türlerinden birine değil.</span><span class="sxs-lookup"><span data-stu-id="d0f52-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="d0f52-121">ReturnType özelliği</span><span class="sxs-lookup"><span data-stu-id="d0f52-121">The ReturnType Property</span></span>  
 <span data-ttu-id="d0f52-122">İçinde sorgu derlendikten sonra bir XPath bir <xref:System.Xml.XPath.XPathExpression> nesne kullanabileceğiniz <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> özelliği <xref:System.Xml.XPath.XPathExpression> ne XPath sorgusu döndürür belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="d0f52-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="d0f52-123"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Özelliği aşağıdakilerden birini döndürür <xref:System.Xml.XPath.XPathResultType> W3C XPath temsil eden numaralandırma değerlerinden dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="d0f52-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="d0f52-124">Aşağıdaki örnekte <xref:System.Xml.XPath.XPathExpression> bir sayı ve bir düğümün kümeden döndürülecek nesne `books.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="d0f52-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="d0f52-125"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Her özellik <xref:System.Xml.XPath.XPathExpression> nesne sonuçlardan yanı sıra <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemleri konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="d0f52-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
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
  
 <span data-ttu-id="d0f52-126">Örnek alan `books.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="d0f52-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="d0f52-127">Daha yüksek performans XPath ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d0f52-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="d0f52-128">Daha iyi performans için sorgularınızdaki olası en belirgin XPath ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0f52-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="d0f52-129">Örneğin, varsa `book` düğümü olan bir alt düğüm `bookstore` düğüm ve `bookstore` düğümü olan XPath ifadesi kullanarak bir XML belgesi en üst öğesi `/bookstore/book` kullanmaktan daha hızlıdır `//book`.</span><span class="sxs-lookup"><span data-stu-id="d0f52-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="d0f52-130">`//book` XPath ifadesi eşleşen düğümleri tanımlamak için XML ağacı kümedeki her düğüm tarayacaktır.</span><span class="sxs-lookup"><span data-stu-id="d0f52-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="d0f52-131">Ayrıca, düğüm tarafından sağlanan gezinme yöntemlerinden kümelerini kullanma <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından sağlanan seçim yöntemini üzerinden geliştirilmiş performans sonuçlanabilir <xref:System.Xml.XPath.XPathNavigator> sınıfı durumlarda, seçim ölçütü burada basittir.</span><span class="sxs-lookup"><span data-stu-id="d0f52-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="d0f52-132">Geçerli düğümünün ilk alt seçmeniz gerekiyorsa, örneğin, kullanılacak daha hızlıdır <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> kullanımı çok yöntemi `child::*[1]` XPath ifadesi ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d0f52-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="d0f52-133">Düğüm hakkında daha fazla bilgi için Gezinti yöntemleri Ayarla <xref:System.Xml.XPath.XPathNavigator> sınıfı [kullanarak düğüm kümesi Gezinti XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="d0f52-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f52-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0f52-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="d0f52-135">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="d0f52-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="d0f52-136">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="d0f52-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="d0f52-137">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="d0f52-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="d0f52-138">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="d0f52-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="d0f52-139">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="d0f52-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="d0f52-140">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="d0f52-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
