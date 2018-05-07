---
title: XML ağaçları (LINQ-XML) değiştirme (C#)
ms.date: 07/20/2015
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
ms.openlocfilehash: 4afb071b5229b3a585ea032effc2985c9a9f7c3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="modifying-xml-trees-linq-to-xml-c"></a>XML ağaçları (LINQ-XML) değiştirme (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir bellek içi bir XML şemasına deposudur. Yüklenemiyor veya bir kaynak XML ağacından ayrıştırılamıyor sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yerinde ağacı değiştirmek ve belki de bir dosyaya kaydetmeyi veya uzak bir sunucuya gönderme ağaç seri hale olanak tanır.  
  
 Yerinde bir ağaç değiştirdiğinizde, bazı yöntemler gibi kullandığınız <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Ancak, işlevsel yapım yeni bir ağaç farklı bir şekilde oluşturmak için kullanılacak olan başka bir yaklaşım yoktur. XML ağacına yapmanız gereken değişiklikleri türlerine bağlı ve ağaç boyutuna bağlı olarak bu yaklaşım, daha sağlam ve geliştirmek daha kolay olabilir. İlk konu bu bölümde, bu iki yaklaşım karşılaştırır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Bellek içi XML Ağacı Değişikliği ve İşlev yapımı (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|İşlev oluşturma için bellek XML ağacında değiştirme karşılaştırır.|  
|[Bir XML ağacına (C#) öğeleri, öznitelikleri ve düğümler ekleme](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Öğe, öznitelik veya düğümleri bir XML ağacına ekleme hakkında bilgi sağlar.|  
|[XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Varolan öğeleri, öznitelikleri veya düğümler değiştirme hakkında bilgi sağlar.|  
|[Bir XML ağacından (C#) öğeleri, öznitelikleri ve düğümleri kaldırma](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|XML ağacından öğeleri, öznitelikleri veya düğümleri kaldırma hakkında bilgi sağlar.|  
|[Bakımı ad/değer çiftleri (C#)](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|En iyi yapılandırma bilgileri veya genel ayarlar gibi ad/değer çiftleri olarak tutulur uygulama bilgilerini korumak açıklar.|  
|[Nasıl yapılır: Namespace değiştirmek için tüm XML ağacı (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Bir XML ağacı bir ad alanından başka bir dosyaya taşıma gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
