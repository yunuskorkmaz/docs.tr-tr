---
description: "Hakkında daha fazla bilgi edinin: Visual Basic XML 'e erişme"
title: XML'e erişme
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 2d77b2aa5f4136095ce5684976fe3ba03be7c28c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462665"
---
# <a name="accessing-xml-in-visual-basic"></a>Visual Basic'de XML'e Erişme

Visual Basic, yapılara erişmek ve bunları gezinmek için XML eksen özellikleri sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Bu özellikler, XML adlarını belirterek öğelere ve özniteliklere erişmenizi sağlamak için özel bir sözdizimi kullanır.  
  
 Aşağıdaki tabloda, Visual Basic XML öğelerine ve özniteliklerine erişmenize olanak tanıyan dil özellikleri listelenmektedir.  
  
### <a name="xml-axis-properties"></a>XML Eksen Özellikleri  
  
|Özellik açıklaması|Örnek|Description|  
|--------------------------|-------------|-----------------|  
|*alt eksen*|`contact.<phone>`|`phone`Öğesinin alt öğesi olan tüm öğeleri alır `contact` .|  
|*öznitelik ekseni*|`phone.@type`|Öğesinin tüm `type` özniteliklerini alır `phone` .|  
|*alt öğe ekseni*|`contacts...<name>`|`name` `contacts` Meydana gelen hiyerarşide ne kadar derinlikte olursa olsun, öğenin tüm öğelerini alır.|  
|*Uzantı Dizin Oluşturucu*|`contacts...<name>(0)`|`name`Sıradaki ilk öğeyi alır.|  
|*değer*|`contacts...<name>.Value`|Dizideki ilk nesnenin dize gösterimini alır veya `Nothing` dizi boşsa.|  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Nasıl yapılır: XML Bağımlı Öğelerine Erişme](how-to-access-xml-descendant-elements.md)  
 Belirtilen bir ada sahip olan ve belirtilen bir XML öğesinin altında bulunan tüm XML öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Alt Öğelerine Erişme](how-to-access-xml-child-elements.md)  
 Bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Özniteliklerine Erişme](how-to-access-xml-attributes.md)  
 Bir XML öğesinde belirtilen bir ada sahip tüm XML özniteliklerine erişmek için bir öznitelik eksen özelliğinin nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: XML Ad Alanı Öneklerini Bildirme ve Kullanma](how-to-declare-and-use-xml-namespace-prefixes.md)  
 XML ad alanı ön ekinin nasıl bildirilemeyeceğini ve XML öğeleri oluşturmak ve ona erişmek için nasıl kullanılacağını gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [XML Eksen Özellikleri](../../../language-reference/xml-axis/index.md)  
 Çeşitli XML erişimi özelliklerini açıklayan bölümlerin bağlantılarını sağlar.  
  
 [Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış](overview-of-linq-to-xml.md)  
 Visual Basic ' de kullanımı için bir giriş sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 [Visual Basic'de XML Oluşturma](creating-xml.md)  
 Visual Basic XML sabit değerlerini kullanmaya giriş sağlar.  
  
 [Visual Basic'de XML'i Düzenleme](manipulating-xml.md)  
 Visual Basic XML 'yi yükleme ve değiştirme hakkındaki bölümlere bağlantılar sağlar.  
  
 [XML](index.md)  
 Visual Basic ' de kullanımı açıklayan bölümlere bağlantılar sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .
