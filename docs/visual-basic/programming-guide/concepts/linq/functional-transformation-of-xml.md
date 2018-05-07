---
title: İşlev dönüştürme XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: c268f414d720bb71866c35de367e9f452f02c5ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="functional-transformation-of-xml-visual-basic"></a>İşlev dönüştürme XML (Visual Basic)
Bu konu, XML belgelerini değiştirme saf işlev dönüştürme yaklaşım açıklar ve yordam bir yaklaşım ile karşılaştırır.  
  
## <a name="modifying-an-xml-document"></a>Bir XML belgesi değiştirme  
 Bir XML programcı için en yaygın görevlerden birini XML bir şekli'ndan diğerine dönüştürme. Bir XML belgesi şekli aşağıdakileri içeren belge yapıdır:  
  
-   Belgenin ifade hiyerarşisi.  
  
-   Öğe ve öznitelik adları.  
  
-   Öğeleri ve özniteliklerinin veri türleri.  
  
 Genel olarak, XML bir şekle dönüştürme en etkili, saf işlevsel dönüşümünün yaklaşımdır. Bu yaklaşımda, birincil Programcı görev tüm XML belge (veya bir veya daha fazla kesinlikle tanımlı düğümleri) uygulanan bir dönüşüm oluşturmaktır. İşlev dönüşümü gerçekleşir tartışmaya açık bir şekilde kod (programcı yaklaşımı hakkında bilgi sahibi olduktan sonra), en kolay en Bakımı yapılabilir kodu üretir ve genellikle daha alternatif yaklaşımlar compact olduğu.  
  
### <a name="xml-functional-transformational-technologies"></a>XML işlevsel Transformational teknolojileri  
 Microsoft XML belgeleri kullanımı için iki işlev dönüştürme teknolojileri sunar: XSLT ve LINQ-XML. XSLT desteklenir <xref:System.Xml.Xsl> yönetilen ad alanı ve yerel MSXML COM uygulama. XSLT XML belgelerini düzenleme için sağlam bir teknoloji olsa da, bir özel etki alanı, XSLT dili ve destekleyici API'lerini uzmanlık gerektirir.  
  
 LINQ-XML, C# veya Visual Basic kodundaki bir açıklayıcı ve güçlü şekilde kodu saf işlevsel dönüştürmeleri için gerekli araçları sağlar. Örneğin, birçok LINQ örnek XML belgeleri için saf bir işlev yaklaşımı kullanın. Ayrıca, [Öğreticisi: düzenleme içerik WordprocessingML belgedeki (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici, kullanırız LINQ-XML işlevsel bir yaklaşım Microsoft Word belgesinde bilgileri işlemek için.  
  
 Daha eksiksiz karşılaştırması LINQ-XML için diğer Microsoft XML teknolojileriyle, bkz: [LINQ-XML vs. Diğer XML teknolojileri](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 Kaynak belge bir düzensiz yapısına sahip olduğunda XSLT belge merkezli dönüştürmeleri için önerilen araçtır. Ancak, LINQ-XML belge merkezli dönüşümler de gerçekleştirebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: XML ağaçlarında XSLT stil (Visual Basic) dönüştürme LINQ'ten kullanım ek açıklamalar](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş saf işlevsel Dönüşümleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)  
 [LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
