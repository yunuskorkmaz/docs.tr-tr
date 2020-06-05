---
title: XML Ağaçlarını Değiştirme (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: 3402188c4e34ef81bad41ed49f9236b4fb7c47ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406891"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bir XML ağacı için bellek içi bir depodır. Bir kaynaktan bir XML ağacını yükledikten veya ayrıştırdıktan sonra, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] söz konusu ağacı yerinde değiştirmenize ve sonra ağacı seri hale getirebilir, belki bir dosyaya kaydederek veya uzak bir sunucuya gönderebilirsiniz.  
  
 Bir ağacı yerinde değiştirdiğinizde, gibi belirli yöntemleri kullanırsınız <xref:System.Xml.Linq.XContainer.Add%2A> .  
  
 Bununla birlikte, farklı bir şekle sahip yeni bir ağaç oluşturmak için işlevsel oluşturma kullanmanın başka bir yaklaşımı de vardır. XML ağacınıza yapmanız gereken değişiklik türlerine bağlı olarak ve ağacın boyutuna bağlı olarak, bu yaklaşım daha sağlam ve daha kolay bir şekilde oluşturulabilir. Bu bölümdeki ilk konu, bu iki yaklaşımı karşılaştırır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu başlığı|Description|  
|-----------|-----------------|  
|[Bellek içi XML ağacı değişikliği ile Işlevsel oluşturma (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md)|Bellekte bir XML ağacının işlevsel yapıya göre değiştirilmesini karşılaştırır.|  
|[XML ağacına öğe, öznitelik ve düğüm ekleme (Visual Basic)](adding-elements-attributes-and-nodes-to-an-xml-tree.md)|XML ağacına öğe, öznitelik veya düğüm ekleme hakkında bilgi sağlar.|  
|[XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme](modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Varolan öğeleri, öznitelikleri veya düğümleri değiştirme hakkında bilgi sağlar.|  
|[Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (Visual Basic)](removing-elements-attributes-and-nodes-from-an-xml-tree.md)|XML ağacından öğeleri, öznitelikleri veya düğümleri kaldırma hakkında bilgi sağlar.|  
|[Ad/değer çiftlerini koruma (Visual Basic)](maintaining-name-value-pairs.md)|Yapılandırma bilgileri veya genel ayarlar gibi ad/değer çiftleri olarak en iyi şekilde tutulan uygulama bilgilerinin nasıl bakımının yapıldığını açıklar.|  
|[Nasıl yapılır: tüm XML ağacının ad alanını değiştirme (Visual Basic)](how-to-change-the-namespace-for-an-entire-xml-tree.md)|Bir XML ağacının bir ad alanından diğerine nasıl taşınacağını gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu (LINQ to XML) (Visual Basic)](programming-guide-linq-to-xml.md)
