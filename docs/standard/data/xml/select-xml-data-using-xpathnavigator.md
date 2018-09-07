---
title: XPathNavigator kullanarak XML verileri seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fea54d36759b12b01fa7a68748d069c7890d84e4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061601"
---
# <a name="select-xml-data-using-xpathnavigator"></a>XPathNavigator kullanarak XML verileri seçme
<xref:System.Xml.XPath.XPathNavigator> Sınıfı bir dizi içinde düğümü seçmek için kullanılan yöntemler kümesi sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath ifadesi kullanarak nesne. Sonra seçili düğümleri kümesini yineleyebilirsiniz.  
  
## <a name="xpathnavigator-selection-methods"></a>XPathNavigator seçimi yöntemleri  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı bir dizi içinde düğümü seçmek için kullanılan yöntemler kümesi sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath ifadesi kullanarak nesne. <xref:System.Xml.XPath.XPathNavigator> Sınıfı bir dizi bir XPath ifadesi kullanarak daha hızlı üst, alt ve alt düğümleri seçmek için en iyi duruma getirilmiş bir yöntem sağlar. Seçili düğümleri kümesini iade bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi veya bir <xref:System.Xml.XPath.XPathNavigator> söz konusu olduğunda tek bir Seçili düğüm nesnesi.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>XPath ifadeleri kullanarak düğümleri seçme  
 Bir dizi bir XPath ifadesi kullanarak düğümü seçmek için aşağıdaki seçimi yöntemlerden birini kullanın.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Çağrıldığında, bu yöntemler serbestçe kullanarak gidebilirsiniz düğümleri kümesini döndürür. bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi veya bir <xref:System.Xml.XPath.XPathNavigator> söz konusu olduğunda tek bir Seçili düğüm nesnesi.  
  
 Gezinme bir <xref:System.Xml.XPath.XPathNodeIterator> nesne konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> oluşturmak için kullanılan nesne. <xref:System.Xml.XPath.XPathNavigator> Döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemlerden döndürülen tek düğümde konumlandırılır ve ayrıca konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> oluşturmak için kullanılan nesne.  
  
 Aşağıdaki örnek, oluşturulmasını gösterir. bir <xref:System.Xml.XPath.XPathNavigator> nesnesinden bir <xref:System.Xml.XPath.XPathDocument> nesnesi, kullanımını <xref:System.Xml.XPath.XPathNavigator.Select%2A> düğümleri seçmek için <xref:System.Xml.XPath.XPathDocument> nesne ve kullanımını <xref:System.Xml.XPath.XPathNodeIterator> seçilen düğümler yineleme yapmak için nesne.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 Örnek alan `books.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>En iyi duruma getirilmiş seçimi yöntemleri  
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> alt öğe, alt ve üst düğümleri almak için kullanılan XPath ifadeleri sınıfını temsil edin. Bu yöntemler, performans için iyileştirilmiş ve onların ilgili XPath ifadeleri hızlıdır. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemler, üst, alt ve alt düğümleri göre seçer bir <xref:System.Xml.XPath.XPathNodeType> değeri veya yerel bir ad ve ad alanı düğümleri seçmek için URI. Seçilen üst, alt ve alt düğümleri döndürülür bir <xref:System.Xml.XPath.XPathNodeIterator> nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [XPath Sorguları ile Tanınan Düğüm Türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [XPath Sorguları ve Ad Alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [Derlenmiş XPath İfadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
