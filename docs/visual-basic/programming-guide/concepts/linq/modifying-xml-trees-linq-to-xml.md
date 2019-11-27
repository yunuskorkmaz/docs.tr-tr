---
title: XML Ağaçlarını Değiştirme (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: c946052beb612c087d26e312875b7f7950ceadf5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353180"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bir XML ağacı için bellek içi depodır. Bir kaynaktan bir XML ağacını yükledikten veya ayrıştırdıktan sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu ağacı yerinde değiştirmenize ve sonra ağacı seri hale getirebilir, belki de bir dosyaya kaydederek veya uzak bir sunucuya göndermenize olanak tanır.  
  
 Bir ağacı yerinde değiştirdiğinizde, <xref:System.Xml.Linq.XContainer.Add%2A>gibi belirli yöntemleri kullanırsınız.  
  
 Bununla birlikte, farklı bir şekle sahip yeni bir ağaç oluşturmak için işlevsel oluşturma kullanmanın başka bir yaklaşımı de vardır. XML ağacınıza yapmanız gereken değişiklik türlerine bağlı olarak ve ağacın boyutuna bağlı olarak, bu yaklaşım daha sağlam ve daha kolay bir şekilde oluşturulabilir. Bu bölümdeki ilk konu, bu iki yaklaşımı karşılaştırır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Bellek içi XML ağacı değişikliği ile Işlevsel oluşturma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Bellekte bir XML ağacının işlevsel yapıya göre değiştirilmesini karşılaştırır.|  
|[XML ağacına öğe, öznitelik ve düğüm ekleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|XML ağacına öğe, öznitelik veya düğüm ekleme hakkında bilgi sağlar.|  
|[XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Varolan öğeleri, öznitelikleri veya düğümleri değiştirme hakkında bilgi sağlar.|  
|[Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|XML ağacından öğeleri, öznitelikleri veya düğümleri kaldırma hakkında bilgi sağlar.|  
|[Ad/değer çiftlerini koruma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Yapılandırma bilgileri veya genel ayarlar gibi ad/değer çiftleri olarak en iyi şekilde tutulan uygulama bilgilerinin nasıl bakımının yapıldığını açıklar.|  
|[Nasıl yapılır: tüm XML ağacının ad alanını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Bir XML ağacının bir ad alanından diğerine nasıl taşınacağını gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
