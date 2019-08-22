---
title: XPath kullanıcıları için LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 5726ce646eba9fce36803ab12e6409b929d3cca5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69667626"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>XPath kullanıcıları için LINQ to XML (Visual Basic)

Bu konu kümesi, bir dizi XPath ifadesini ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerlerini gösterir.  
  
 Örneklerin hepsi, içindeki uzantı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>yöntemleri tarafından kullanılabilir hale getirilen ' deki XPath işlevselliğini kullanır. Örneklerde hem XPath ifadesi hem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] de ifadesi yürütülür. Her bir örnek, her iki sorgunun sonucunu, XPath ifadesinin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguya işlevsel olarak denk olduğunu doğrulayarak karşılaştırır. Her iki sorgu türü de aynı XML ağacından düğüm döndürmekle birlikte, sorgu sonucu karşılaştırması başvuru kimliği kullanılarak yapılır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[XPath ile LINQ to XML Karşılaştırması](../../../../visual-basic/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]arasındaki benzerlikler ve farklılıklara genel bakış sunar.|  
|[Nasıl yapılır: Bir alt öğe bulun (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|XPath alt öğe eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> yöntemiyle karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"DeliveryNotes"`.|  
|[Nasıl yapılır: Alt öğelerin bir listesini bulun (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|XPath alt öğe eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> ekseniyle karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./*"`|  
|[Nasıl yapılır: Kök öğeyi bul (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XPath ile kök öğenin nasıl alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"/PurchaseOrders"`|  
|[Nasıl yapılır: Alt öğeleri bul (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile belirli bir ada sahip olan alt öğelerin nasıl alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"//Name"`|  
|[Nasıl yapılır: Öznitelik üzerinde filtreleme (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Belirtilen bir ada sahip ve XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile belirtilen bir değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./Address[@Type='Shipping']"`|  
|[Nasıl yapılır: Ilgili öğeleri bul (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]diğer bir öğenin değeri tarafından başvurulan bir öznitelik üzerinde seçim yapma şeklini karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Nasıl yapılır: Ad alanındaki öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace.md)|XML ad alanları ile çalışma için <xref:System.Xml.XmlNamespaceManager> <xref:System.Xml.Linq.XName> sınıfının <xref:System.Xml.Linq.XName.Namespace%2A> özelliğiyle XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfının kullanımını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./aw:*"`|  
|[Nasıl yapılır: Önceki eşdüzey öğeleri bul (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|XPath `preceding-sibling` eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] alt ekseniylekarşılaştırır.<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> İlişkili XPath ifadesi:`"preceding-sibling::*"`|  
|[Nasıl yapılır: Alt öğenin alt öğelerini bul (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile belirli bir ada sahip bir alt öğenin alt öğelerinin nasıl alınacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./Paragraph//Text/text()"`|  
|[Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath.md)|XPath <code>&#124;</code> 'tekiUNION[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]işlecinin kullanımını, içindeki Standartsorguişleciylekarşılaştırır.<xref:System.Linq.Enumerable.Concat%2A><br /><br /> İlişkili XPath ifadesi:<code>"//Category&#124;//Price"</code>|  
|[Nasıl yapılır: Eşdüzey düğümleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]içindeki belirli bir ada sahip bir düğümün tüm eşdüzey öğelerinin nasıl bulunacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"../Book"`|  
|[Nasıl yapılır: Üst öğenin bir özniteliğini bulun (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Üst öğeye gitmeyi ve XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak ilişkili bir özniteliği bulmayı karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"../@id"`|  
|[Nasıl yapılır: Belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bul (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bağlam düğümünün eşdüzey öğelerinin belirli özniteliklerinin nasıl bulunacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"../Book/@id"`|  
|[Nasıl yapılır: Belirli bir özniteliğe sahip öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak belirli bir özniteliği içeren al öğelerinin nasıl bulunacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./*[@Select]"`|  
|[Nasıl yapılır: Konuma göre alt öğeleri bul (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak göreli konumuna göre bir öğe bulmayı karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"Test[position() >= 2 and position() <= 4]"`|  
|[Nasıl yapılır: Hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak bir düğümün hemen önceki eşdüzey öğesinin nasıl bulunacağını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [XML ağaçlarını sorgulama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
