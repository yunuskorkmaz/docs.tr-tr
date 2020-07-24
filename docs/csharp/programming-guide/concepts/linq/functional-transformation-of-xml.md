---
title: XML işlevsel dönüştürmesi (C#)
description: C# ' deki saf işlevsel dönüştürme yaklaşımını kullanarak XML belgelerinin nasıl değiştirileceğini ve bunun bir yordamsal yaklaşımdan nasıl farklı olduğunu öğrenin.
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 4ccc6859f3663eb3760c7faeaf115a5e88a2278a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103665"
---
# <a name="functional-transformation-of-xml-c"></a>XML işlevsel dönüştürmesi (C#)
Bu konu, XML belgelerini değiştirmeye yönelik saf işlevsel dönüşüm yaklaşımını ve bunu bir yordamsal yaklaşımla karşıtlıkları ele alır.  
  
## <a name="modifying-an-xml-document"></a>XML belgesini değiştirme  
 Bir XML programcı için en yaygın görevlerden biri, XML 'yi bir şekilden diğerine dönüştürmeye yöneliktir. XML belgesinin şekli, belgenin yapısıdır ve şunları içerir:  
  
- Belge tarafından ifade edilen hiyerarşi.  
  
- Öğe ve öznitelik adları.  
  
- Öğelerin ve özniteliklerin veri türleri.  
  
 Genellikle, XML 'yi bir şekilden diğerine dönüştürmek için en etkili yaklaşım, saf işlevsel dönüşümden biridir. Bu yaklaşımda, birincil programcı görevi tüm XML belgesine (veya bir veya daha fazla tanımlanmış düğüme) uygulanan bir dönüşüm oluşturmaktır. İşlevsel dönüşüm, kodun en kolay kodu (programcılar yaklaşımı öğrendikten sonra), en çok sürdürülebilir kodu oluşturur ve genellikle diğer yaklaşımlardan daha küçük olur.  
  
### <a name="xml-functional-transformational-technologies"></a>XML Işlev dönüştürme teknolojileri  
 Microsoft, XML belgelerinde kullanılmak üzere iki işlevsel dönüştürme teknolojisi sunar: XSLT ve LINQ to XML. XSLT, <xref:System.Xml.Xsl> yönetilen ad alanında ve MSXML 'nin yerel com uygulamasında desteklenir. XSLT, XML belgelerinin işlenmesine yönelik sağlam bir teknoloji olsa da, XSLT dili ve destekleyici API 'Leri gibi özelleştirilmiş bir etki alanında uzmanlık gerektirir.  
  
 LINQ to XML, saf işlevsel dönüştürmeleri C# veya Visual Basic kodu dahilinde bir ifade ve güçlü bir şekilde kodladığı araçları sağlar. Örneğin, LINQ to XML belgelerindeki birçok örnek, saf işlevsel bir yaklaşım kullanır. Ayrıca [öğreticide, bir WordprocessingML belgesi (C#) öğreticisinde Içerik düzenleme](./shape-of-wordprocessingml-documents.md) , bir Microsoft Word belgesindeki bilgileri işlemek için LINQ to XML işlevsel bir yaklaşımda kullanıyoruz.  
  
 Diğer Microsoft XML teknolojileriyle LINQ to XML daha kapsamlı bir karşılaştırması için, bkz. [LINQ to XML vs. DIĞER XML Teknolojileri](./linq-to-xml-vs-other-xml-technologies.md).  
  
XSLT, kaynak belge düzensiz bir yapıya sahip olduğunda belge merkezli dönüşümler için önerilen araçtır. Ancak, LINQ to XML belge merkezli dönüşümler de yapabilir. Daha fazla bilgi için bkz. [XSLT stilinde LINQ to XML ağaçlarını dönüştürmek için ek açıklamalar kullanma (C#)](./how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel dönüşümlere giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (C#)](./shape-of-wordprocessingml-documents.md)
- [LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması](./linq-to-xml-vs-other-xml-technologies.md)
