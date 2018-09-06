---
title: Visual Basic'de XML'e Erişme
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 0540c52cf3e4cd7594f051c10832ea99cf58a34e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734388"
---
# <a name="accessing-xml-in-visual-basic"></a>Visual Basic'de XML'e Erişme
Visual Basic, XML eksen özellikleri erişmek ve gezinme sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapıları. Bu özellikler, öğeler ve öznitelikler XML adları belirterek erişim sağlamak için özel bir söz dizimi kullanın.  
  
 Aşağıdaki tablo, XML öğeleri ve özniteliklerinin Visual Basic'te erişmenize olanak sağlayan dil özellikleri listeler.  
  
### <a name="xml-axis-properties"></a>XML Eksen Özellikleri  
  
|Özellik açıklaması|Örnek|Açıklama|  
|--------------------------|-------------|-----------------|  
|*alt eksen*|`contact.<phone>`|Tüm alır `phone` alt öğeleri olan öğeler `contact` öğesi.|  
|*öznitelik eksen*|`phone.@type`|Tüm alır `type` özniteliklerini `phone` öğesi.|  
|*alt eksen*|`contacts...<name>`|Tüm alır `name` öğelerini `contacts` bağımsız olarak hiyerarşideki ortaya nasıl derin bir öğe.|  
|*uzantı dizin oluşturucu*|`contacts...<name>(0)`|İlk alır `name` serisinden öğesi.|  
|*value*|`contacts...<name>.Value`|İlk nesnenin dize gösterimini sırada alır veya `Nothing` Serisi boşsa.|  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: XML Bağımlı Öğelerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Descendant axis özelliği belirtilen ada sahip ve belirtilen bir XML öğesi altında içerdiği tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Alt Öğelerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Belirtilen ada sahip bir XML öğesi tüm XML alt öğelerine erişmek için axis özelliği bir alt kullanmayı gösterir.  
  
 [Nasıl yapılır: XML Özniteliklerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Belirtilen ada sahip bir XML öğesi tüm XML özniteliklerini erişmek için bir özniteliği axis özelliği kullanmayı gösterir.  
  
 [Nasıl yapılır: XML Ad Alanı Öneklerini Bildirme ve Kullanma](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Bir XML ad alanı öneki bildirin ve XML öğeleri oluşturma ve kullanma işlemi gösterilmektedir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML Eksen Özellikleri](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Çeşitli XML erişim özelliklerini açıklayan bölümlerin bağlantılarını sağlar.  
  
 [LINQ to XML Visual Basic'de genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Kullanarak bir giriş sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic'te.  
  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Visual Basic'de XML değişmez değerlerini kullanarak bir giriş sağlar.  
  
 [Visual Basic'de XML düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Yükleme ve Visual Basic'te XML değiştirme hakkında bölümlerine bağlantılar sağlar.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Nasıl kullanılacağını açıklayan bölümlerin bağlantılarını sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic'te.
