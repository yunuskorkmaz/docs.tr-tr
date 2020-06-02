---
title: XPathNavigator Kullanarak XML Verileri Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: d5e7074fc8c68a0a0243ea4ad237e713e0a729b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289063"
---
# <a name="select-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verileri Seçme
Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> XPath ifadesi kullanarak bir veya nesnesindeki düğüm kümesi seçmek için kullanılan bir yöntemler kümesi sağlar <xref:System.Xml.XmlDocument> . Seçili düğüm kümesi üzerinde yineleme yapabilirsiniz.  
  
## <a name="xpathnavigator-selection-methods"></a>XPathNavigator seçim yöntemleri  
 Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> XPath ifadesi kullanarak bir veya nesnesindeki düğüm kümesi seçmek için kullanılan bir yöntemler kümesi sağlar <xref:System.Xml.XmlDocument> . <xref:System.Xml.XPath.XPathNavigator>Sınıfı ayrıca, bir XPath ifadesi kullanmaktan daha hızlı üst, alt ve alt düğümleri seçmek için iyileştirilmiş bir yöntemler kümesi sağlar. Seçili düğüm kümesi, <xref:System.Xml.XPath.XPathNodeIterator> <xref:System.Xml.XPath.XPathNavigator> tek bir seçili düğüm olması durumunda bir nesne veya nesne içinde döndürülür.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>XPath Ifadeleri kullanarak düğüm seçme  
 Bir XPath ifadesi kullanarak bir düğüm kümesi seçmek için aşağıdaki seçim yöntemlerinden birini kullanın.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Çağrıldığında, bu yöntemler bir <xref:System.Xml.XPath.XPathNodeIterator> nesne veya <xref:System.Xml.XPath.XPathNavigator> tek bir seçili düğüm durumunda bir nesne kullanarak serbestçe gezinebileceğiniz bir düğüm kümesi döndürür.  
  
 Bir nesneyle gezinmek, <xref:System.Xml.XPath.XPathNodeIterator> <xref:System.Xml.XPath.XPathNavigator> onu oluşturmak için kullanılan nesnenin konumunu etkilemez. <xref:System.Xml.XPath.XPathNavigator>Metotlardan döndürülen nesne, <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> tek döndürülen düğümde konumlandırılır ve ayrıca <xref:System.Xml.XPath.XPathNavigator> onu oluşturmak için kullanılan nesnenin konumunu etkilemez.  
  
 Aşağıdaki örnek, bir nesneden bir nesnenin oluşturulmasını <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> , <xref:System.Xml.XPath.XPathNavigator.Select%2A> nesne içindeki düğümleri seçmek için yönteminin kullanımını <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XPath.XPathNodeIterator> seçilen düğümlerin üzerinde yinelemek için nesnesinin kullanımını gösterir.  
  
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
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>Sınıfının, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri, <xref:System.Xml.XPath.XPathNavigator> Genel, alt ve üst düğümleri almak Için yaygın olarak kullanılan XPath ifadelerini temsil eder. Bu yöntemler performans için iyileştirilmiştir ve bunlara karşılık gelen XPath ifadelerinden daha hızlıdır. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri bir <xref:System.Xml.XPath.XPathNodeType> değere veya seçilecek düğümlerin yerel adına ve ad alanı URI 'sine göre üst, alt ve alt düğümleri seçer. Seçili üst öğe, alt ve alt düğümleri bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesinde döndürülür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](matching-nodes-using-xpathnavigator.md)
- [XPath Sorguları ile Tanınan Düğüm Türleri](node-types-recognized-with-xpath-queries.md)
- [XPath Sorguları ve Ad Alanları](xpath-queries-and-namespaces.md)
- [Derlenmiş XPath İfadeleri](compiled-xpath-expressions.md)
