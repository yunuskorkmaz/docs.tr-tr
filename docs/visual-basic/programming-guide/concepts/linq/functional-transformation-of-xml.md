---
title: XML İşlevsel Dönüşümü
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: 7e029fd562ae3f221a8aaef40f332a1e3fa896eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353418"
---
# <a name="functional-transformation-of-xml-visual-basic"></a>XML işlevsel dönüştürmesi (Visual Basic)
Bu konu, XML belgelerini değiştirmeye yönelik saf işlevsel dönüşüm yaklaşımını ve bunu bir yordamsal yaklaşımla karşıtlıkları ele alır.  
  
## <a name="modifying-an-xml-document"></a>XML belgesini değiştirme  
 Bir XML programcı için en yaygın görevlerden biri, XML 'yi bir şekilden diğerine dönüştürmeye yöneliktir. XML belgesinin şekli, belgenin yapısıdır ve şunları içerir:  
  
- Belge tarafından ifade edilen hiyerarşi.  
  
- Öğe ve öznitelik adları.  
  
- Öğelerin ve özniteliklerin veri türleri.  
  
 Genellikle, XML 'yi bir şekilden diğerine dönüştürmek için en etkili yaklaşım, saf işlevsel dönüşümden biridir. Bu yaklaşımda, birincil programcı görevi tüm XML belgesine (veya bir veya daha fazla tanımlanmış düğüme) uygulanan bir dönüşüm oluşturmaktır. İşlevsel dönüşüm, kodun en kolay kodu (programcılar yaklaşımı öğrendikten sonra), en çok sürdürülebilir kodu oluşturur ve genellikle diğer yaklaşımlardan daha küçük olur.  
  
### <a name="xml-functional-transformational-technologies"></a>XML Işlev dönüştürme teknolojileri  
 Microsoft, XML belgelerinde kullanılmak üzere iki işlevsel dönüştürme teknolojisi sunar: XSLT ve LINQ to XML. XSLT, <xref:System.Xml.Xsl> yönetilen ad alanında ve MSXML 'nin yerel COM uygulamasında desteklenir. XSLT, XML belgelerinin işlenmesine yönelik sağlam bir teknoloji olsa da, XSLT dili ve destekleyici API 'Leri gibi özelleştirilmiş bir etki alanında uzmanlık gerektirir.  
  
 LINQ to XML, saf işlevsel dönüştürmeleri bir ifade ve güçlü bir biçimde, kod içinde C# veya Visual Basic kodda kodladığı araçları sağlar. Örneğin, LINQ to XML belgelerindeki birçok örnek, saf işlevsel bir yaklaşım kullanır. Ayrıca [öğreticide, bir WordprocessingML belgesi (Visual Basic) öğreticisindeki Içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) , bir Microsoft Word belgesindeki bilgileri işlemek için LINQ to XML işlevsel bir yaklaşımda kullanıyoruz.  
  
 Diğer Microsoft XML teknolojileriyle LINQ to XML daha kapsamlı bir karşılaştırması için, bkz. [LINQ to XML vs. DIĞER XML Teknolojileri](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT, kaynak belge düzensiz bir yapıya sahip olduğunda belge merkezli dönüşümler için önerilen araçtır. Ancak, LINQ to XML belge merkezli dönüşümler de yapabilir. Daha fazla bilgi için bkz. [nasıl yapılır: XSLT stilinde LINQ to XML ağaçlarını dönüştürmek Için ek açıklamaları kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel dönüşümlere giriş (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [LINQ to XML ve diğer XML Teknolojileri](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
