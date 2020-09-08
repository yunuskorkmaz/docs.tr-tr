---
title: XML-LINQ to XML işlevsel dönüştürmesi
description: XML belgelerini değiştirme ve bir yordamsal yaklaşımdan farklılık gösteren saf işlevsel dönüştürme yaklaşımı hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: b23288e013a4104b21523e17e1f266a9f712c451
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553016"
---
# <a name="functional-transformation-of-xml-linq-to-xml"></a>XML işlevsel dönüştürmesi (LINQ to XML)

Bu makalede, XML belgelerini değiştirme ve bir yordamsal yaklaşımla karşıtın saf işlevsel dönüşüm yaklaşımı ele alınmaktadır.

## <a name="modifying-an-xml-document"></a>XML belgesini değiştirme

Bir XML programcı için en yaygın görevlerden biri, XML 'yi bir şekilden diğerine dönüştürmeye yöneliktir. XML belgesinin şekli, belgenin yapısıdır ve şunları içerir:

- Belge tarafından ifade edilen hiyerarşi.
- Öğe ve öznitelik adları.
- Öğelerin ve özniteliklerin veri türleri.

Genellikle, XML 'yi bir şekilden diğerine dönüştürmek için en etkili yaklaşım, saf işlevsel dönüşümden biridir. Bu yaklaşımda, birincil programcı görevi tüm XML belgesine (veya bir veya daha fazla tanımlanmış düğüme) uygulanan bir dönüşüm oluşturmaktır. İşlevsel dönüşüm, kodun en kolay kodu (programcılar yaklaşımı öğrendikten sonra), en çok sürdürülebilir kodu oluşturur ve genellikle diğer yaklaşımlardan daha küçük olur.

### <a name="xml-functional-transformational-technologies"></a>XML işlev dönüştürme teknolojileri

Microsoft, XML belgelerinde kullanılmak üzere iki işlevsel dönüştürme teknolojisi sunar: XSLT ve LINQ to XML. XSLT, <xref:System.Xml.Xsl> yönetilen ad alanında ve MSXML 'nin yerel com uygulamasında desteklenir. XSLT, XML belgelerinin işlenmesine yönelik sağlam bir teknoloji olsa da, XSLT dili ve destekleyici API 'Leri gibi özelleştirilmiş bir etki alanında uzmanlık gerektirir.

LINQ to XML, saf işlevsel dönüştürmeleri C# veya Visual Basic kodu dahilinde bir ifade ve güçlü bir şekilde kodladığı araçları sağlar. Örneğin, LINQ to XML belgelerindeki birçok örnek, saf işlevsel bir yaklaşım kullanır. Ayrıca [öğreticide, bir WordprocessingML belge öğreticisinde Içerik düzenleme](xml-shape-wordprocessingml-documents.md) , bir Microsoft Word belgesindeki bilgileri işlemek için LINQ to XML işlevsel bir yaklaşımda kullanıyoruz.

Diğer Microsoft XML teknolojileriyle LINQ to XML daha kapsamlı bir karşılaştırması için, bkz. [LINQ to XML vs. DIĞER XML Teknolojileri](linq-xml-vs-xml-technologies.md).

XSLT, kaynak belge düzensiz bir yapıya sahip olduğunda belge merkezli dönüşümler için önerilen araçtır. Ancak, LINQ to XML belge merkezli dönüşümler de yapabilir. Daha fazla bilgi için bkz. [BIR XSLT stilinde LINQ to XML ağaçlarını dönüştürmek için ek açıklamalar kullanma](use-annotations-transform-linq-xml-trees-xslt-style.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Saf işlevsel dönüşümlere giriş](introduction-pure-functional-transformations.md)
- [Öğretici: WordprocessingML belgesinde içerik Işleme](xml-shape-wordprocessingml-documents.md)
- [LINQ to XML ve diğer XML Teknolojileri](linq-xml-vs-xml-technologies.md)
