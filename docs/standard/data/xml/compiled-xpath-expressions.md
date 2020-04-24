---
title: Derlenmiş XPath İfadeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: b4675765849299050eb6cddeaaa497bc6cdc620a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711109"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="f4735-102">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f4735-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="f4735-103"><xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathExpression.Compile%2A> Nesnesi, <xref:System.Xml.XPath.XPathExpression> sınıfının statik yönteminden veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> <xref:System.Xml.XPath.XPathNavigator> sınıfın yöntemine döndürülen bir derlenmiş XPath sorgusunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f4735-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="f4735-104">XPathExpression sınıfı</span><span class="sxs-lookup"><span data-stu-id="f4735-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="f4735-105">Aynı XPath sorgusu birden çok kez kullanılıyorsa <xref:System.Xml.XPath.XPathExpression> , bir nesneyle temsil edilen derlenmiş bir XPath sorgusu faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4735-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="f4735-106">Örneğin, her seferinde XPath sorgusunu <xref:System.Xml.XPath.XPathNavigator.Select%2A> temsil eden bir dize kullanmak yerine, yöntemi birden çok kez çağırırken sınıfın <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemini <xref:System.Xml.XPath.XPathExpression> veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemini kullanın ve daha sonra kullanmak üzere bir <xref:System.Xml.XPath.XPathExpression> nesnede XPath sorgusunu derleyip önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="f4735-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="f4735-107">Derlendikten sonra <xref:System.Xml.XPath.XPathExpression> nesne, XPath sorgusundan döndürülen türe bağlı olarak aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemlerine giriş olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4735-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="f4735-108">Aşağıdaki tabloda, W3C XPath dönüş türlerinin her biri, Microsoft .NET Framework equivalencies ve <xref:System.Xml.XPath.XPathExpression> nesnenin dönüş türüne göre hangi yöntemleri kullanılabileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4735-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="f4735-109">W3C XPath dönüş türü</span><span class="sxs-lookup"><span data-stu-id="f4735-109">W3C XPath Return Type</span></span>|<span data-ttu-id="f4735-110">.NET Framework eşdeğer tür</span><span class="sxs-lookup"><span data-stu-id="f4735-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="f4735-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4735-111">Description</span></span>|<span data-ttu-id="f4735-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f4735-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="f4735-113">Belge düzeninde oluşturulan yinelemeler olmadan sıralanmamış bir düğüm koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f4735-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="f4735-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> veya <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="f4735-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="f4735-115">Bir `true` veya `false` değeri.</span><span class="sxs-lookup"><span data-stu-id="f4735-115">A `true` or `false` value.</span></span>|<span data-ttu-id="f4735-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> veya</span><span class="sxs-lookup"><span data-stu-id="f4735-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="f4735-117">Kayan noktalı sayı.</span><span class="sxs-lookup"><span data-stu-id="f4735-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="f4735-118">Bir UCS karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="f4735-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <span data-ttu-id="f4735-119">Yöntemi <xref:System.Xml.XPath.XPathNavigator.Matches%2A> , parametresi olarak bir XPath ifadesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f4735-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="f4735-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Yöntemi W3C XPath dönüş <xref:System.Xml.XPath.XPathNavigator> türlerinden birini değil bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4735-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="f4735-121">ReturnType Özelliği</span><span class="sxs-lookup"><span data-stu-id="f4735-121">The ReturnType Property</span></span>  
 <span data-ttu-id="f4735-122">Bir XPath sorgusu bir <xref:System.Xml.XPath.XPathExpression> nesneye derlendikten sonra, XPath sorgusunun döndürdüğü şeyi belirlemek için <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> <xref:System.Xml.XPath.XPathExpression> nesnesinin özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4735-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="f4735-123"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> ÖZELLIĞI, W3C XPath dönüş türlerini temsil <xref:System.Xml.XPath.XPathResultType> eden aşağıdaki sabit listesi değerlerinden birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4735-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="f4735-124">Aşağıdaki örnek, `books.xml` dosyasından bir <xref:System.Xml.XPath.XPathExpression> sayı ve bir düğüm kümesi döndürmek için nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4735-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="f4735-125">Her <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> <xref:System.Xml.XPath.XPathExpression> nesnenin özelliğinin yanı sıra <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemlerinin sonuçları da konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="f4735-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
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
  
 <span data-ttu-id="f4735-126">Örnek, `books.xml` dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="f4735-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="f4735-127">Daha yüksek performans XPath Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f4735-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="f4735-128">Daha iyi performans için, sorgularınızda olası en belirli XPath ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4735-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="f4735-129">Örneğin, `book` düğüm `bookstore` düğümün bir alt DÜĞÜMÜDÜR ve `bookstore` düğüm bir XML belgesindeki en üstteki öğe ise, XPath ifadesinin `/bookstore/book` kullanılması kullanmaktan `//book`daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="f4735-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="f4735-130">`//book` XPath ifadesi, eşleşen düğümleri BELIRLEMEK için XML ağacındaki her düğümü tarar.</span><span class="sxs-lookup"><span data-stu-id="f4735-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="f4735-131">Ayrıca, <xref:System.Xml.XPath.XPathNavigator> sınıf tarafından sağlanan düğüm kümesi gezinme yöntemlerinin kullanılması, seçim ölçütlerinizin basit olduğu durumlarda <xref:System.Xml.XPath.XPathNavigator> sınıfının sağladığı seçim yöntemlerine göre performansın iyileşmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4735-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="f4735-132">Örneğin, geçerli düğümün ilk alt öğesini seçmeniz gerekiyorsa, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> yöntemi `child::*[1]` XPath ifadesini ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemini kullanmak için kullanmak daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="f4735-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="f4735-133"><xref:System.Xml.XPath.XPathNavigator> Sınıfın düğüm kümesi gezinti yöntemleri hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak düğüm kümesi gezintisi](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="f4735-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4735-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4735-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f4735-135">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="f4735-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f4735-136">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="f4735-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f4735-137">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f4735-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="f4735-138">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="f4735-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="f4735-139">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="f4735-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="f4735-140">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="f4735-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
