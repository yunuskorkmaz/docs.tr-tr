---
title: Derlenmiş XPath İfadeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: e74b52e471699fc663504fa42d6c7e502859adda
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291532"
---
# <a name="compiled-xpath-expressions"></a>Derlenmiş XPath İfadeleri
<xref:System.Xml.XPath.XPathExpression>Nesnesi, <xref:System.Xml.XPath.XPathExpression.Compile%2A> sınıfının statik yönteminden <xref:System.Xml.XPath.XPathExpression> veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> sınıfın yöntemine döndürülen bir derlenmiş XPath sorgusunu temsil eder <xref:System.Xml.XPath.XPathNavigator> .  
  
## <a name="the-xpathexpression-class"></a>XPathExpression sınıfı  
 Aynı XPath sorgusu birden çok kez kullanılıyorsa, bir nesneyle temsil edilen derlenmiş bir XPath sorgusu <xref:System.Xml.XPath.XPathExpression> faydalıdır.  
  
 Örneğin, <xref:System.Xml.XPath.XPathNavigator.Select%2A> her seferinde XPath sorgusunu temsil eden bir dize kullanmak yerine, yöntemi birden çok kez çağırırken sınıfın <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemini <xref:System.Xml.XPath.XPathExpression> veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> sınıf yöntemini kullanın <xref:System.Xml.XPath.XPathNavigator> ve daha sonra kullanmak üzere bir nesnede XPath sorgusunu derleyip önbelleğe alma <xref:System.Xml.XPath.XPathExpression> .  
  
 Derlendikten sonra <xref:System.Xml.XPath.XPathExpression> nesne, <xref:System.Xml.XPath.XPathNavigator> XPath sorgusundan döndürülen türe bağlı olarak aşağıdaki sınıf yöntemlerine giriş olarak kullanılabilir.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Aşağıdaki tabloda, W3C XPath dönüş türlerinin her biri, Microsoft .NET Framework equivalencies ve <xref:System.Xml.XPath.XPathExpression> nesnenin dönüş türüne göre hangi yöntemleri kullanılabileceği açıklanmaktadır.  
  
|W3C XPath dönüş türü|.NET Framework eşdeğer tür|Description|Yöntemler|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Belge düzeninde oluşturulan yinelemeler olmadan sıralanmamış bir düğüm koleksiyonu.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> veya <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|Bir `true` veya `false` değeri.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> veya<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Kayan noktalı sayı.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Bir UCS karakter dizisi.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, parametresi olarak bir XPath ifadesini kabul eder. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>YÖNTEMI <xref:System.Xml.XPath.XPathNavigator> W3C XPath dönüş türlerinden birini değil bir nesne döndürür.  
  
### <a name="the-returntype-property"></a>ReturnType Özelliği  
 Bir XPath sorgusu bir nesneye derlendikten sonra <xref:System.Xml.XPath.XPathExpression> , <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> <xref:System.Xml.XPath.XPathExpression> XPath sorgusunun döndürdüğü şeyi belirlemek için nesnesinin özelliğini kullanabilirsiniz.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A>Özelliği, <xref:System.Xml.XPath.XPathResultType> W3C XPath dönüş türlerini temsil eden aşağıdaki sabit listesi değerlerinden birini döndürür.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 Aşağıdaki örnek, <xref:System.Xml.XPath.XPathExpression> dosyasından bir sayı ve bir düğüm kümesi döndürmek için nesnesini kullanır `books.xml` . <xref:System.Xml.XPath.XPathExpression.ReturnType%2A>Her <xref:System.Xml.XPath.XPathExpression> nesnenin özelliğinin yanı sıra ve yöntemlerinin sonuçları da <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> <xref:System.Xml.XPath.XPathNavigator.Select%2A> konsoluna yazılır.  
  
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
  
 Örnek, `books.xml` dosyayı giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Daha yüksek performans XPath Ifadeleri  
 Daha iyi performans için, sorgularınızda olası en belirli XPath ifadesini kullanın. Örneğin, düğüm `book` düğümün bir alt düğümüdür `bookstore` ve `bookstore` düğüm bir XML belgesindeki en üstteki öğe ise, XPath ifadesinin kullanılması `/bookstore/book` kullanmaktan daha hızlıdır `//book` . `//book`XPath ifadesi, eşleşen düğümleri belirlemek IÇIN XML ağacındaki her düğümü tarar.  
  
 Ayrıca, sınıf tarafından sağlanan düğüm kümesi gezinme yöntemlerinin kullanılması, <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator> seçim ölçütlerinizin basit olduğu durumlarda sınıfının sağladığı seçim yöntemlerine göre performansın iyileşmesine neden olabilir. Örneğin, geçerli düğümün ilk alt öğesini seçmeniz gerekiyorsa, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> yöntemi `child::*[1]` XPath ifadesini ve yöntemini kullanmak için kullanmak daha hızlıdır <xref:System.Xml.XPath.XPathNavigator.Select%2A> .  
  
 Sınıfın düğüm kümesi gezinti yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPathNavigator kullanarak düğüm kümesi gezintisi](node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](matching-nodes-using-xpathnavigator.md)
- [XPath Sorguları ile Tanınan Düğüm Türleri](node-types-recognized-with-xpath-queries.md)
- [XPath Sorguları ve Ad Alanları](xpath-queries-and-namespaces.md)
