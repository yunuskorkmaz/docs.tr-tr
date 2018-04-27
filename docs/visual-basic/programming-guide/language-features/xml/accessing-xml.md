---
title: Visual Basic'de XML'e Erişme
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 064e4b224d37172b8f79e57c73164b90186ef922
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="accessing-xml-in-visual-basic"></a>Visual Basic'de XML'e Erişme
Visual Basic sağlar erişmek ve gezinme XML eksen özellikleri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapıları. Bu özellikler, öğeleri ve özniteliklerinin XML adları belirterek erişim sağlamak için özel bir sözdizimi kullanın.  
  
 XML öğeleri ve öznitelikleri Visual Basic'te erişmenize olanak sağlayan dil özellikler aşağıdaki tabloda listelenmektedir.  
  
### <a name="xml-axis-properties"></a>XML Eksen Özellikleri  
  
|Özellik açıklaması|Örnek|Açıklama|  
|--------------------------|-------------|-----------------|  
|*alt eksen*|`contact.<phone>`|Tüm alır `phone` alt öğeleri olan öğeler `contact` öğesi.|  
|*öznitelik eksen*|`phone.@type`|Tüm alır `type` özniteliklerini `phone` öğesi.|  
|*descendant axis*|`contacts...<name>`|Tüm alır `name` öğeleri `contacts` oluşma hiyerarşideki nasıl derin bakılmaksızın öğesi.|  
|*uzantı dizin oluşturucu*|`contacts...<name>(0)`|İlk alır `name` serisinden öğesi.|  
|*value*|`contacts...<name>.Value`|İlk nesnenin dize gösterimini sırayla alır veya `Nothing` dizisi boşsa.|  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: XML Bağımlı Öğelerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Descendant axis özelliği, belirtilen ada sahip ve belirtilen bir XML öğesi altında bulunan tüm XML öğeleri erişmek için nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Alt Öğelerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Bir alt kullanmak bir XML öğesi belirtilen ada sahip tüm XML alt öğelerine erişmek için axis özelliği gösterilmektedir.  
  
 [Nasıl yapılır: XML Özniteliklerine Erişme](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Attribute axis özelliği bir XML öğesi belirtilen ada sahip tüm XML öznitelikleri erişmek için nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Ad Alanı Öneklerini Bildirme ve Kullanma](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Bir XML ad alanı öneki bildirme ve oluşturma ve XML öğeleri erişmek için nasıl kullanılacağını gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML Eksen Özellikleri](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 Çeşitli XML erişim özelliklerini açıklayan bölümlerin bağlantılarını sağlar.  
  
 [LINQ-XML Visual Basic'de genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Kullanarak bir giriş sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic'te.  
  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Visual Basic'te XML değişmez değerleri kullanmaya giriş bilgileri sağlar.  
  
 [Visual Basic'te XML düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Yükleme ve Visual Basic'te XML değiştirme hakkında bölümlerine bağlantılar sağlar.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Nasıl kullanılacağını açıklayan bölümlerin bağlantılarını sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic'te.
