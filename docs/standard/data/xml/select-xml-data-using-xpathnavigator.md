---
title: XPathNavigator Kullanarak XML Verileri Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 99b6b3b6959abf4c8adc313364ad641249bd9bc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710173"
---
# <a name="select-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verileri Seçme
Sınıfı <xref:System.Xml.XPath.XPathNavigator> , bir XPath ifadesi kullanarak bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğüm kümesi seçmek için kullanılan bir yöntemler kümesi sağlar. Seçili düğüm kümesi üzerinde yineleme yapabilirsiniz.  
  
## <a name="xpathnavigator-selection-methods"></a>XPathNavigator seçim yöntemleri  
 Sınıfı <xref:System.Xml.XPath.XPathNavigator> , bir XPath ifadesi kullanarak bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğüm kümesi seçmek için kullanılan bir yöntemler kümesi sağlar. <xref:System.Xml.XPath.XPathNavigator> Sınıfı ayrıca, bir XPath ifadesi kullanmaktan daha hızlı üst, alt ve alt düğümleri seçmek için iyileştirilmiş bir yöntemler kümesi sağlar. Seçili düğüm kümesi, tek bir seçili düğüm olması <xref:System.Xml.XPath.XPathNodeIterator> durumunda bir nesne <xref:System.Xml.XPath.XPathNavigator> veya nesne içinde döndürülür.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>XPath Ifadeleri kullanarak düğüm seçme  
 Bir XPath ifadesi kullanarak bir düğüm kümesi seçmek için aşağıdaki seçim yöntemlerinden birini kullanın.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Çağrıldığında, bu yöntemler bir <xref:System.Xml.XPath.XPathNodeIterator> nesne veya tek bir seçili düğüm durumunda bir <xref:System.Xml.XPath.XPathNavigator> nesne kullanarak serbestçe gezinebileceğiniz bir düğüm kümesi döndürür.  
  
 Bir <xref:System.Xml.XPath.XPathNodeIterator> nesneyle gezinmek, onu oluşturmak için kullanılan <xref:System.Xml.XPath.XPathNavigator> nesnenin konumunu etkilemez. Metotlardan döndürülen <xref:System.Xml.XPath.XPathNavigator> nesne, tek döndürülen düğümde konumlandırılır ve ayrıca onu oluşturmak için kullanılan <xref:System.Xml.XPath.XPathNavigator> nesnenin konumunu etkilemez. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <xref:System.Xml.XPath.XPathNavigator> Aşağıdaki örnek, bir <xref:System.Xml.XPath.XPathDocument> nesneden bir nesnenin oluşturulmasını, <xref:System.Xml.XPath.XPathNavigator.Select%2A> <xref:System.Xml.XPath.XPathDocument> nesne içindeki düğümleri seçmek için yönteminin kullanımını ve seçilen düğümlerin üzerinde yinelemek için <xref:System.Xml.XPath.XPathNodeIterator> nesnesinin kullanımını gösterir.  
  
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
  
 Örnek, `books.xml` dosyayı giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>İyileştirilmiş seçim yöntemleri  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfının <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri, genel, alt ve üst düğümleri almak için yaygın olarak kullanılan XPath ifadelerini temsil eder. Bu yöntemler performans için iyileştirilmiştir ve bunlara karşılık gelen XPath ifadelerinden daha hızlıdır. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri bir <xref:System.Xml.XPath.XPathNodeType> değere veya seçilecek düğümlerin yerel adına ve ad alanı URI 'sine göre üst, alt ve alt düğümleri seçer. Seçili üst öğe, alt ve alt düğümleri bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesinde döndürülür.  
  
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
