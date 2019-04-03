---
title: LINQ to XML için XPath kullanıcıları (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 13c23eec1261700b15bea7f92f6c50e9231e900a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824253"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML için XPath kullanıcıları (Visual Basic)

Bu konu başlıkları birkaç XPath ifadeleri gösterir ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerleri.  
  
 Tüm örneklerin XPath işlevleri kullanmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapılan kullanılabilir alanında uzantı yöntemlerini tarafından <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>. XPath ifadesi örnekleri yürütün ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ifade. Her örnek XPath ifadesi işlevsel olarak eşdeğer olduğunu doğrulama, iki sorguların sonuçlarını sonra karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu. Her iki sorgu türleri aynı XML ağacından düğümleri geri döndürür gibi sorgu sonucu karşılaştırma başvuru kimliği kullanılarak yapılır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[XPath ile LINQ to XML Karşılaştırması](../../../../visual-basic/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|XPath arasındaki benzerlikleri ve genel bir bakış sağlar ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Nasıl yapılır: Bulma (XPath-LINQ to XML) bir alt öğesi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|XPath alt öğe eksene karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi.<br /><br /> İlgili XPath ifadesidir:`"DeliveryNotes"`.|  
|[Nasıl yapılır: Bulma (XPath-LINQ to XML) alt öğeleri listesi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|XPath alt öğeleri eksene karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni.<br /><br /> İlgili XPath ifadesidir:`"./*"`|  
|[Nasıl yapılır: Bulma (XPath-LINQ to XML) kök öğesi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|XPath kök öğesiyle alma karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"/PurchaseOrders"`|  
|[Nasıl yapılır: (XPath-LINQ to XML) alt öğeleri bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|XPath ile belirli bir ada sahip alt öğeleri almak nasıl karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"//Name"`|  
|[Nasıl yapılır: Filtreleme (XPath-LINQ to XML) öznitelik (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Belirtilen ada sahip ve XPath ile belirtilen bir değere sahip bir öznitelik ile alt öğeleri almak nasıl karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`".//Address[@Type='Shipping']"`|  
|[Nasıl yapılır: (XPath-LINQ to XML) ilgili öğeleri bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|XPath ile başka bir öğenin değeri tarafından başvurulan öznitelik bir öğe seçtiğinizde alma karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Nasıl yapılır: Bir Namespace (XPath-LINQ to XML) içindeki öğeleri bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace.md)|XPath kullanımını karşılaştırır <xref:System.Xml.XmlNamespaceManager> sınıfıyla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> özelliği <xref:System.Xml.Linq.XName> sınıfı için XML ad alanları ile çalışma.<br /><br /> İlgili XPath ifadesidir:`"./aw:*"`|  
|[Nasıl yapılır: Önceki eşdüzey (XPath-LINQ to XML) bulunamadı (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|XPath karşılaştırır `preceding-sibling` eksene [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] alt <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> ekseni.<br /><br /> İlgili XPath ifadesidir:`"preceding-sibling::*"`|  
|[Nasıl yapılır: Bir alt öğesi (XPath-LINQ to XML) alt öğeleri bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|XPath ile belirli bir ada sahip bir alt öğenin alt öğeleri almak nasıl karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"./Paragraph//Text/text()"`|  
|[Nasıl yapılır: (XPath-LINQ to XML) iki konum yolunun birleşimini bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath.md)|Birleşim işleci kullanımını karşılaştırır <code>&#124;</code>, XPath ile <xref:System.Linq.Enumerable.Concat%2A> standart sorgu işleci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:<code>"//Category&#124;//Price"</code>|  
|[Nasıl yapılır: (XPath-LINQ to XML) eşdüzey düğümleri bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|XPath ile belirli bir ada sahip bir düğüm tüm eşdüzeyi bulma karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"../Book"`|  
|[Nasıl yapılır: Bir (XPath-LINQ to XML) üst öğenin özniteliğini bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Üst öğeye gidin ve XPath kullanarak ilişkili bir öznitelik karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"../@id"`|  
|[Nasıl yapılır: (XPath-LINQ to XML) belirli bir ada sahip eşdüzeylerin özniteliklerini bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name.md)|Eşdüzey bağlam düğümünün XPath ile belirli öznitelikleri bulmak amacıyla nasıl karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"../Book/@id"`|  
|[Nasıl yapılır: (XPath-LINQ to XML) belirli bir özniteliğe sahip öğeleri bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute.md)|XPath kullanarak belirli bir öznitelik içeren al öğelerin nasıl bulunacağını karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"./*[@Select]"`|  
|[Nasıl yapılır: Konum (XPath-LINQ to XML) göre alt öğeleri bulma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position.md)|XPath kullanarak kendi göreli konumlarına göre bir öğeyi bulmak nasıl karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"Test[position() >= 2 and position() <= 4]"`|  
|[Nasıl yapılır: Önceki eşdüzeyi (XPath-LINQ to XML) bulunamadı (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|XPath kullanarak bir düğümün önceki eşdüzeyi bulma karşılaştırır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> İlgili XPath ifadesidir:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [(Visual Basic) XML ağaçlarını sorgulama](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
