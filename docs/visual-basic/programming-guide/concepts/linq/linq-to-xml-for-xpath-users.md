---
title: XPath Kullanıcıları için LINQ to XML
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 4d5749e72acc8b051db2180b751051696ae04d57
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345464"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>XPath kullanıcıları için LINQ to XML (Visual Basic)

Bu konu kümesi, bir dizi XPath ifadesini ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerlerini gösterir.  
  
 Örneklerin hepsi, <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>uzantı yöntemleri tarafından kullanılabilir hale getirilen [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XPath işlevselliğini kullanır. Örneklerde hem XPath ifadesi hem de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ifadesi yürütülür. Her bir örnek, her iki sorgunun sonucunu, XPath ifadesinin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgusuna işlevsel olarak denk olduğunu doğrulayarak karşılaştırır. Her iki sorgu türü de aynı XML ağacından düğüm döndürmekle birlikte, sorgu sonucu karşılaştırması başvuru kimliği kullanılarak yapılır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[XPath ile LINQ to XML Karşılaştırması](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]arasındaki benzerlikler ve farklılıklara genel bakış sunar.|  
|[Nasıl yapılır: alt öğe bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|XPath alt öğe eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> yöntemiyle karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"DeliveryNotes"`.|  
|[Nasıl yapılır: alt öğelerin bir listesini bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|XPath alt öğeleri eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni ile karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./*"`|  
|[Nasıl yapılır: kök öğeyi bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nasıl kök öğe alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"/PurchaseOrders"`|  
|[Nasıl yapılır: alt öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile belirli bir ada sahip alt öğelerin nasıl alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"//Name"`|  
|[Nasıl yapılır: bir özniteliğe filtre uygulama (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Belirtilen bir ada sahip ve XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./Address[@Type='Shipping']"`|  
|[Nasıl yapılır: Ilgili öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]başka bir öğenin değeri tarafından başvurulan bir öznitelik üzerinde seçim yaparak nasıl bir öğe alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Nasıl yapılır: ad alanındaki öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace.md)|XML ad alanları ile çalışma için, XPath <xref:System.Xml.XmlNamespaceManager> sınıfının kullanımını <xref:System.Xml.Linq.XName> sınıfının [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> özelliği ile karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./aw:*"`|  
|[Nasıl yapılır: önceki eşdüzey öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|XPath `preceding-sibling` eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] alt <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> ekseniyle karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"preceding-sibling::*"`|  
|[Nasıl yapılır: bir alt öğenin alt öğelerini bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile belirli bir ada sahip bir alt öğenin alt öğelerinin nasıl alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./Paragraph//Text/text()"`|  
|[Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath.md)|XPath 'teki <code>&#124;</code>Union işlecinin kullanımını, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<xref:System.Linq.Enumerable.Concat%2A> standart sorgu işleci ile karşılaştırır.<br /><br /> İlişkili XPath ifadesi:<code>"//Category&#124;//Price"</code>|  
|[Nasıl yapılır: eşdüzey düğümleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]belirli bir ada sahip bir düğümün tüm eşdüzey öğelerinin nasıl bulunacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"../Book"`|  
|[Nasıl yapılır: üst öğenin bir özniteliğini bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Üst öğeye gitmeyi ve XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak ilişkili bir özniteliği bulmayı karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"../@id"`|  
|[Nasıl yapılır: belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile bağlam düğümünün eşdüzey öğelerinin belirli özniteliklerini bulmayı karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"../Book/@id"`|  
|[Nasıl yapılır: belirli bir özniteliğe sahip öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak belirli bir özniteliği içeren al öğelerinin nasıl bulunacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./*[@Select]"`|  
|[Nasıl yapılır: konuma göre alt öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak göreli konumuna göre bir öğe bulmayı karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"Test[position() >= 2 and position() <= 4]"`|  
|[Nasıl yapılır: hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak bir düğümün hemen önceki eşdüzey öğesini bulmayı karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [XML ağaçlarını sorgulama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
