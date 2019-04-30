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
# <a name="compiled-xpath-expressions"></a>Derlenmiş XPath İfadeleri
Bir <xref:System.Xml.XPath.XPathExpression> nesneyi temsil ediyor öğesinden döndürülen statik olarak derlenmiş bir XPath sorgusu <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> sınıfı veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
## <a name="the-xpathexpression-class"></a>XPathExpression sınıfı  
 Bir XPath sorgusu tarafından temsil edilen derlenmiş bir <xref:System.Xml.XPath.XPathExpression> nesne, aynı XPath sorgusu birden çok kez kullanılıyorsa kullanışlıdır.  
  
 Örneğin, çağrılırken <xref:System.Xml.XPath.XPathNavigator.Select%2A> XPath sorgusu her zaman temsil eden bir dize kullanmak yerine, birden çok kez yöntemini kullanın <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> sınıfı veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> derlemek için sınıf ve XPath sorgusundaki önbelleğe bir <xref:System.Xml.XPath.XPathExpression> yeniden kullanımı ve performansı nesnesi.  
  
 Bir kez derlenmesinin sonra <xref:System.Xml.XPath.XPathExpression> nesne, aşağıdaki giriş olarak kullanılabilir <xref:System.Xml.XPath.XPathNavigator> türüne bağlı olarak sınıfı yöntemleri XPath sorgusundan döndürülen.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Aşağıdaki tablo W3C XPath dönüş türleri, kendi Microsoft .NET Framework Eşitlikleri ve hangi açıklar yöntemleri <xref:System.Xml.XPath.XPathExpression> nesne kullanılabilir olan kendi dönüş türüne göre.  
  
|W3C XPath dönüş türü|.NET framework eşdeğeri türü|Açıklama|Yöntemler|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Belge sırada oluşturulan çoğaltmaları olmadan düğümler sırasız bir koleksiyonu.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> veya <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|A `true` veya `false` değeri.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> veya<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Bir kayan noktalı sayı.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|UCS karakter dizisi.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi bir XPath ifadesi, parametre olarak kabul eder. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Yöntemi döndürür bir <xref:System.Xml.XPath.XPathNavigator> nesnesi, W3C XPath dönüş türlerinden birine değil.  
  
### <a name="the-returntype-property"></a>ReturnType özelliği  
 İçinde sorgu derlendikten sonra bir XPath bir <xref:System.Xml.XPath.XPathExpression> nesne kullanabileceğiniz <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> özelliği <xref:System.Xml.XPath.XPathExpression> ne XPath sorgusu döndürür belirlemek için nesne.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Özelliği aşağıdakilerden birini döndürür <xref:System.Xml.XPath.XPathResultType> W3C XPath temsil eden numaralandırma değerlerinden dönüş türü.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 Aşağıdaki örnekte <xref:System.Xml.XPath.XPathExpression> bir sayı ve bir düğümün kümeden döndürülecek nesne `books.xml` dosya. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Her özellik <xref:System.Xml.XPath.XPathExpression> nesne sonuçlardan yanı sıra <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemleri konsoluna yazılır.  
  
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
  
 Örnek alan `books.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Daha yüksek performans XPath ifadeleri  
 Daha iyi performans için sorgularınızdaki olası en belirgin XPath ifadesi kullanın. Örneğin, varsa `book` düğümü olan bir alt düğüm `bookstore` düğüm ve `bookstore` düğümü olan XPath ifadesi kullanarak bir XML belgesi en üst öğesi `/bookstore/book` kullanmaktan daha hızlıdır `//book`. `//book` XPath ifadesi eşleşen düğümleri tanımlamak için XML ağacı kümedeki her düğüm tarayacaktır.  
  
 Ayrıca, düğüm tarafından sağlanan gezinme yöntemlerinden kümelerini kullanma <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından sağlanan seçim yöntemini üzerinden geliştirilmiş performans sonuçlanabilir <xref:System.Xml.XPath.XPathNavigator> sınıfı durumlarda, seçim ölçütü burada basittir. Geçerli düğümünün ilk alt seçmeniz gerekiyorsa, örneğin, kullanılacak daha hızlıdır <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> kullanımı çok yöntemi `child::*[1]` XPath ifadesi ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemi.  
  
 Düğüm hakkında daha fazla bilgi için Gezinti yöntemleri Ayarla <xref:System.Xml.XPath.XPathNavigator> sınıfı [kullanarak düğüm kümesi Gezinti XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
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
