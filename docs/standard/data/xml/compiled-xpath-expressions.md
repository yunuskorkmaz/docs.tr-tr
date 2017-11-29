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
# <a name="compiled-xpath-expressions"></a>Derlenmiş XPath ifadeleri
Bir <xref:System.Xml.XPath.XPathExpression> nesneyi temsil ediyor herhangi birinden statik döndürülen derlenmiş bir XPath sorgusu <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> sınıfı veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
## <a name="the-xpathexpression-class"></a>XPathExpression sınıfı  
 Bir XPath sorgusu tarafından temsil edilen derlenmiş bir <xref:System.Xml.XPath.XPathExpression> nesnesidir aynı XPath sorgusu birden çok kez kullanılıyorsa yararlı.  
  
 Örneğin, çağrılırken <xref:System.Xml.XPath.XPathNavigator.Select%2A> XPath sorgusu her zaman temsil eden bir dize kullanmak yerine, birden çok kez yöntemi kullanın <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> sınıfı veya <xref:System.Xml.XPath.XPathNavigator.Compile%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> derlemek için sınıf ve XPath sorgusunda önbelleğe bir <xref:System.Xml.XPath.XPathExpression> yeniden ve performansı nesnesi.  
  
 Bir kez derlenmiş <xref:System.Xml.XPath.XPathExpression> nesnesi, aşağıdaki girdi olarak kullanılabilecek <xref:System.Xml.XPath.XPathNavigator> türüne bağlı olarak sınıfı yöntemleri XPath sorgudan döndürülen.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Aşağıdaki tabloda her W3C XPath dönüş türleri, kendi Microsoft .NET Framework Eşitlikleri ve ne açıklanmaktadır yöntemleri <xref:System.Xml.XPath.XPathExpression> nesnesi kullanılabilir ile dönüş türüne göre.  
  
|W3C XPath dönüş türü|.NET framework eşdeğeri türü|Açıklama|Yöntemler|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Belge sırada oluşturulan çoğaltmaları olmadan düğümler sırasız bir koleksiyonu.|<xref:System.Xml.XPath.XPathNavigator.Select%2A>veya<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|A `true` veya `false` değeri.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>veya<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Bir kayan noktalı sayı.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|UCS bir karakter dizisi.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi bir XPath ifadesi, parametre olarak kabul eder. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Yöntemi döndürür bir <xref:System.Xml.XPath.XPathNavigator> nesnesi, W3C XPath dönüş türleri birini değil.  
  
### <a name="the-returntype-property"></a>ReturnType özelliği  
 İçine sorgu derlendikten sonra XPath bir <xref:System.Xml.XPath.XPathExpression> nesne kullanabileceğiniz <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> özelliği <xref:System.Xml.XPath.XPathExpression> ne XPath sorgusu döndürür belirlemek için nesne.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Özelliği aşağıdakilerden birini döndürür <xref:System.Xml.XPath.XPathResultType> W3C XPath temsil eden numaralandırma değerlerinden dönüş türü.  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 Aşağıdaki örnek kullanır <xref:System.Xml.XPath.XPathExpression> bir sayı ve kümeden bir düğümü döndürmek için nesne `books.xml` dosya. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Her özellik <xref:System.Xml.XPath.XPathExpression> nesne sonuçlarından yanı sıra <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemleri konsoluna yazılır.  
  
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
  
 Örnek alır `books.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Daha yüksek performans XPath ifadeleri  
 Daha iyi performans için sorgularınızda olası en belirgin XPath ifadesi kullanın. Örneğin, varsa `book` düğümdür alt düğümü `bookstore` düğümü ve `bookstore` düğümdür XPath ifadesini kullanarak bir XML belgesi en üstteki öğe `/bookstore/book` kullanmaktan daha hızlıdır `//book`. `//book` XPath ifadesi eşleşen düğümleri tanımlamak için XML ağaç kümedeki her düğüm tarama.  
  
 Ayrıca, düğüm tarafından sağlanan gezinti yöntemlerini kümelerini kullanma <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından sağlanan seçim yöntemlerini üzerinden geliştirilmiş performans sonuçlanabilir <xref:System.Xml.XPath.XPathNavigator> seçim kriterleri nerede basit durumlarda sınıfı. Geçerli düğüm ilk alt öğesini seçmeniz gerekir, örneğin, kullanılacak hızlıdır <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> kullanımı çok yöntemi `child::*[1]` XPath ifadesi ve <xref:System.Xml.XPath.XPathNavigator.Select%2A> yöntemi.  
  
 Düğüm hakkında daha fazla bilgi için gezinti yöntemlerini ayarlayın <xref:System.Xml.XPath.XPathNavigator> sınıfı için bkz: [düğüm kümesi Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath veri modelini kullanarak işlem XML verileri](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XML verileri XPathNavigator kullanarak seçin](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [XPath XPathNavigator kullanarak ifadeler değerlendir](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Eşleşen düğümleri XPathNavigator kullanma](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath sorguları tanınan düğüm türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [XPath sorguları ve ad alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
