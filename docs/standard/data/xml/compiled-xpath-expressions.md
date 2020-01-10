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
# <a name="compiled-xpath-expressions"></a>Derlenmiş XPath İfadeleri
<xref:System.Xml.XPath.XPathExpression> nesnesi, <xref:System.Xml.XPath.XPathExpression> sınıfının statik <xref:System.Xml.XPath.XPathExpression.Compile%2A> yönteminden veya <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yönteminin döndürdüğü derlenmiş XPath sorgusunu temsil eder.  
  
## <a name="the-xpathexpression-class"></a>XPathExpression sınıfı  
 Aynı XPath sorgusu birden çok kez kullanılıyorsa, bir <xref:System.Xml.XPath.XPathExpression> nesnesi tarafından temsil edilen derlenmiş bir XPath sorgusu faydalıdır.  
  
 Örneğin, her seferinde XPath sorgusunu temsil eden bir dize kullanmak yerine <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemi birden çok kez çağrılırken, <xref:System.Xml.XPath.XPathExpression> sınıfının <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemini veya <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemini kullanarak, yeniden kullanım ve gelişmiş performans için bir <xref:System.Xml.XPath.XPathExpression> nesnesinde XPath sorgusunu derleyip önbelleğe alma.  
  
 Derlendikten sonra, <xref:System.Xml.XPath.XPathExpression> nesnesi, XPath sorgusundan döndürülen türe bağlı olarak aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıfı yöntemlerine giriş olarak kullanılabilir.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Aşağıdaki tabloda, her bir W3C XPath dönüş türü, Microsoft .NET Framework equivalencies ve <xref:System.Xml.XPath.XPathExpression> nesnesinin, dönüş türüne göre hangi yöntemleri kullanılabileceği açıklanmaktadır.  
  
|W3C XPath dönüş türü|.NET Framework eşdeğer tür|Açıklama|Yöntemler|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Belge düzeninde oluşturulan yinelemeler olmadan sıralanmamış bir düğüm koleksiyonu.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> veya <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|Bir `true` veya `false` değeri.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> veya<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Kayan noktalı sayı.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Bir UCS karakter dizisi.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi, parametresi olarak bir XPath ifadesini kabul eder. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemi, W3C XPath dönüş türlerinden birini değil, bir <xref:System.Xml.XPath.XPathNavigator> nesnesi döndürür.  
  
### <a name="the-returntype-property"></a>ReturnType Özelliği  
 Bir XPath sorgusu bir <xref:System.Xml.XPath.XPathExpression> nesnesine derlendikten sonra, XPath sorgusunun döndürdüğü şeyi belirlemek için <xref:System.Xml.XPath.XPathExpression> nesnesinin <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> özelliğini kullanabilirsiniz.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> özelliği, W3C XPath dönüş türlerini temsil eden aşağıdaki <xref:System.Xml.XPath.XPathResultType> sabit listesi değerlerinden birini döndürür.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 Aşağıdaki örnek, `books.xml` dosyasından bir sayı ve düğüm kümesi döndürmek için <xref:System.Xml.XPath.XPathExpression> nesnesini kullanır. Her <xref:System.Xml.XPath.XPathExpression> nesnesinin <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> özelliği ve <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> sonuçları ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemleri konsola yazılır.  
  
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
  
 Örnek, `books.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Daha yüksek performans XPath Ifadeleri  
 Daha iyi performans için, sorgularınızda olası en belirli XPath ifadesini kullanın. Örneğin, `book` düğümü `bookstore` düğümünün bir alt düğümüdür ve `bookstore` düğümü bir XML belgesindeki en üstteki öğe ise, XPath ifadesi `/bookstore/book` kullanarak `//book`kullanmaktan daha hızlıdır. `//book` XPath ifadesi, eşleşen düğümleri belirlemek için XML ağacındaki her düğümü tarar.  
  
 Ayrıca, <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından sağlanan düğüm kümesi gezinme yöntemlerinin kullanılması, seçim ölçütlerinizin basit olduğu durumlarda <xref:System.Xml.XPath.XPathNavigator> sınıfının sağladığı seçim yöntemlerine göre daha fazla performans oluşmasına neden olabilir. Örneğin, geçerli düğümün ilk alt öğesini seçmeniz gerekiyorsa, `child::*[1]` XPath ifadesini ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemini kullanmak için <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> yönteminin kullanılması daha hızlıdır.  
  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının düğüm kümesi gezinti yöntemleri hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak düğüm kümesi gezintisi](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [XPath Sorguları ile Tanınan Düğüm Türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [XPath Sorguları ve Ad Alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
