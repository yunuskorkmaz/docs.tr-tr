---
title: XML'e erişme
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351743"
---
# <a name="accessing-xml-in-visual-basic"></a>Visual Basic'de XML'e Erişme
Visual Basic, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapılarına erişmek ve bunları gezinmek için XML eksen özellikleri sağlar. Bu özellikler, XML adlarını belirterek öğelere ve özniteliklere erişmenizi sağlamak için özel bir sözdizimi kullanır.  
  
 Aşağıdaki tabloda, Visual Basic XML öğelerine ve özniteliklerine erişmenize olanak tanıyan dil özellikleri listelenmektedir.  
  
### <a name="xml-axis-properties"></a>XML Eksen Özellikleri  
  
|Özellik açıklaması|Örnek|Açıklama|  
|--------------------------|-------------|-----------------|  
|*alt eksen*|`contact.<phone>`|`contact` öğesinin alt öğesi olan tüm `phone` öğelerini alır.|  
|*öznitelik ekseni*|`phone.@type`|`phone` öğesinin tüm `type` özniteliklerini alır.|  
|*alt öğe ekseni*|`contacts...<name>`|`contacts` öğesinin tüm `name` öğelerini alır ve bu hiyerarşide ne kadar derinlikte olursa olsun.|  
|*Uzantı Dizin Oluşturucu*|`contacts...<name>(0)`|Sıradaki ilk `name` öğeyi alır.|  
|*value*|`contacts...<name>.Value`|Dizideki ilk nesnenin dize gösterimini alır veya dizi boşsa `Nothing`.|  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: XML Bağımlı Öğelerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Belirtilen bir ada sahip olan ve belirtilen bir XML öğesinin altında bulunan tüm XML öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Alt Öğelerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Özniteliklerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Bir XML öğesinde belirtilen bir ada sahip tüm XML özniteliklerine erişmek için bir öznitelik eksen özelliğinin nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Ad Alanı Öneklerini Bildirme ve Kullanma](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 XML ad alanı ön ekinin nasıl bildirilemeyeceğini ve XML öğeleri oluşturmak ve ona erişmek için nasıl kullanılacağını gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML Eksen Özellikleri](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Çeşitli XML erişimi özelliklerini açıklayan bölümlerin bağlantılarını sağlar.  
  
 [Visual Basic LINQ to XML genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanımı için bir giriş sağlar.  
  
 [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Visual Basic XML sabit değerlerini kullanmaya giriş sağlar.  
  
 [Visual Basic XML 'yi düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Visual Basic XML 'yi yükleme ve değiştirme hakkındaki bölümlere bağlantılar sağlar.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanımını açıklayan bölümlerin bağlantılarını sağlar.
