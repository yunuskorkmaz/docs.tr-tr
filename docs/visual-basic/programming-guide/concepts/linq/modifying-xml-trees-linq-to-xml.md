---
title: (LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: e524088ac6ccde3a46de7547379eb82f9760fd57
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959529"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>(LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir bellek içi XML ağacı için deposudur. Yükleme veya ayrıştırma bir kaynaktan bir XML ağacı sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] o ağaç yerinde değiştirebilir ve belki de bir dosyaya kaydetme veya uzak bir sunucuya gönderme ağacı seri hale getirme olanak tanır.  
  
 Yerinde bir ağaç değiştirdiğinizde, belirli yöntemler gibi kullanın <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Ancak, farklı bir şekilde yeni bir ağaç oluşturmak için işlev yapım kullanılacak olan başka bir yaklaşım yoktur. Ve bağlı olarak, XML ağacına yapmanız gereken değişiklik türlerini ağaç boyutuna bağlı olarak, bu yaklaşım daha sağlam ve geliştirmeyi daha kolay olabilir. İlk konu bu bölümde, bu iki yaklaşımı karşılaştırır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Bellek içi XML Ağacı Değişikliği ve İşlevsel oluşturma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|İşlevsel oluşturma bellekte bir XML ağacı değiştirme karşılaştırır.|  
|[(Visual Basic) XML ağacına öğe, öznitelik ve düğümleri ekleme](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|XML ağacına öğe, öznitelik veya düğümleri ekleme hakkında bilgi sağlar.|  
|[XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Var olan öğeleri, öznitelikleri ve düğümleri değiştirme hakkında bilgi sağlar.|  
|[(Visual Basic) XML ağacından öğe, öznitelik ve düğümleri kaldırma](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|XML ağacından öğe, öznitelik veya düğümleri kaldırma hakkında bilgi sağlar.|  
|[Ad/değer çiftleri (Visual Basic) sağlama](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|En iyi yapılandırma bilgileri veya genel ayarlar gibi bir ad/değer çiftleri olarak tutulur, uygulama bilgilerini korumak nasıl açıklar.|  
|[Nasıl yapılır: Namespace değiştirmek tüm XML ağacının için (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Bir XML ağacı bir ad alanından diğerine taşımak gösterilmektedir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
