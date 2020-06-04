---
title: XPath Kullanıcıları için LINQ to XML
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 7942d33831644875f390e9128965fe1c36433808
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368796"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>XPath kullanıcıları için LINQ to XML (Visual Basic)

Bu konu kümesi, bir dizi XPath ifadesini ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerlerini gösterir.  
  
 Örneklerin hepsi, içindeki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Uzantı yöntemleri tarafından kullanılabilir hale getirilen ' deki XPath işlevselliğini kullanır <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> . Örneklerde hem XPath ifadesi hem de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ifadesi yürütülür. Her bir örnek, her iki sorgunun sonucunu, XPath ifadesinin sorguya işlevsel olarak denk olduğunu doğrulayarak karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Her iki sorgu türü de aynı XML ağacından düğüm döndürmekle birlikte, sorgu sonucu karşılaştırması başvuru kimliği kullanılarak yapılır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu başlığı|Description|  
|-----------|-----------------|  
|[XPath ile LINQ to XML Karşılaştırması](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|XPath ve arasındaki benzerlikler ve farklılıklara genel bakış sunar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .|  
|[Nasıl yapılır: alt öğe bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-child-element-xpath-linq-to-xml.md)|XPath alt öğe eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> yöntemiyle karşılaştırır.<br /><br /> İlişkili XPath ifadesi: `"DeliveryNotes"` .|  
|[Nasıl yapılır: alt öğelerin bir listesini bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|XPath alt öğe eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> ekseniyle karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./*"`|  
|[Nasıl yapılır: kök öğeyi bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-root-element-xpath-linq-to-xml.md)|XPath ve XPath ile kök öğenin nasıl alınacağını karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"/PurchaseOrders"`|  
|[Nasıl yapılır: alt öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendant-elements-xpath-linq-to-xml.md)|XPath ve ile belirli bir ada sahip olan alt öğelerin nasıl alınacağını karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"//Name"`|  
|[Nasıl yapılır: bir özniteliğe filtre uygulama (XPath-LINQ to XML) (Visual Basic)](how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Belirtilen bir ada sahip ve XPath ile belirtilen bir değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"./Address[@Type='Shipping']"`|  
|[Nasıl yapılır: Ilgili öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-related-elements-xpath-linq-to-xml.md)|XPath ve diğer bir öğenin değeri tarafından başvurulan bir öznitelik üzerinde seçim yapma şeklini karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"./Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Nasıl yapılır: ad alanındaki öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-in-a-namespace.md)|<xref:System.Xml.XmlNamespaceManager> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> <xref:System.Xml.Linq.XName> XML ad alanları ile çalışma için sınıfının özelliğiyle XPath sınıfının kullanımını karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"./aw:*"`|  
|[Nasıl yapılır: önceki eşdüzey öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-preceding-siblings-xpath-linq-to-xml.md)|XPath `preceding-sibling` eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] alt <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> ekseniyle karşılaştırır.<br /><br /> İlişkili XPath ifadesi:`"preceding-sibling::*"`|  
|[Nasıl yapılır: bir alt öğenin alt öğelerini bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|XPath ve ile belirli bir ada sahip bir alt öğenin alt öğelerinin nasıl alınacağını karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"./Paragraph//Text/text()"`|  
|[Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-union-of-two-location-paths-xpath.md)|XPath 'teki UNION işlecinin kullanımını, <code>&#124;</code> <xref:System.Linq.Enumerable.Concat%2A> içindeki standart sorgu işleciyle karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:<code>"//Category&#124;//Price"</code>|  
|[Nasıl yapılır: eşdüzey düğümleri bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-sibling-nodes-xpath-linq-to-xml.md)|XPath ve içindeki belirli bir ada sahip bir düğümün tüm eşdüzey öğelerinin nasıl bulunacağını karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"../Book"`|  
|[Nasıl yapılır: üst öğenin bir özniteliğini bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Üst öğeye gitmeyi ve XPath ve kullanarak ilişkili bir özniteliği bulmayı karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"../@id"`|  
|[Nasıl yapılır: belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-attributes-of-siblings-with-a-specific-name.md)|XPath ve bağlam düğümünün eşdüzey öğelerinin belirli özniteliklerinin nasıl bulunacağını karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"../Book/@id"`|  
|[Nasıl yapılır: belirli bir özniteliğe sahip öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-with-a-specific-attribute.md)|XPath ve kullanarak belirli bir özniteliği içeren al öğelerinin nasıl bulunacağını karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"./*[@Select]"`|  
|[Nasıl yapılır: konuma göre alt öğeleri bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-child-elements-based-on-position.md)|XPath ve kullanarak göreli konumuna göre bir öğe bulmayı karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"Test[position() >= 2 and position() <= 4]"`|  
|[Nasıl yapılır: hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|XPath ve kullanarak bir düğümün hemen önceki eşdüzey öğesinin nasıl bulunacağını karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> İlişkili XPath ifadesi:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [XML ağaçlarını sorgulama (Visual Basic)](querying-xml-trees.md)
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
