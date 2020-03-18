---
title: XML'nin Fonksiyonel Dönüşümü (C#)
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 83ecd97f9319027dc50f346abf7a9888b5c23862
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75336804"
---
# <a name="functional-transformation-of-xml-c"></a>XML'nin Fonksiyonel Dönüşümü (C#)
Bu konu, XML belgelerini değiştirmek için saf işlevsel dönüşüm yaklaşımını tartışır ve bunu bir yordam yaklaşımıyla karşılaştırır.  
  
## <a name="modifying-an-xml-document"></a>XML Belgesini Değiştirme  
 Bir XML programcısı için en yaygın görevlerden biri XML'i bir şekilden diğerine dönüştürmektir. XML belgesinin şekli, belgenin aşağıdakileri içeren yapısıdır:  
  
- Belge tarafından ifade edilen hiyerarşi.  
  
- Öğe ve öznitelik adları.  
  
- Öğelerin ve özniteliklerin veri türleri.  
  
 Genel olarak, XML'i bir şekilden diğerine dönüştürmek için en etkili yaklaşım saf işlevsel dönüşümdür. Bu yaklaşımda, birincil programcı görevi, xml belgesinin tamamına (veya bir veya daha fazla kesin olarak tanımlanmış düğümlere) uygulanan bir dönüşüm oluşturmaktır. İşlevsel dönüşüm muhtemelen kodlamak için en kolay olandır (bir programcı yaklaşıma aşina olduktan sonra), en çok korunabilir kodu verir ve genellikle alternatif yaklaşımlardan daha kompakttır.  
  
### <a name="xml-functional-transformational-technologies"></a>XML Fonksiyonel Dönüşüm Teknolojileri  
 Microsoft, XML belgelerinde kullanılmak üzere iki işlevsel dönüşüm teknolojisi sunar: XSLT ve LINQ'dan XML'e kadar. XSLT <xref:System.Xml.Xsl> yönetilen ad alanında ve MSXML'in yerel COM uygulamasında desteklenir. XSLT, XML belgelerini manipüle etmek için sağlam bir teknoloji olmasına rağmen, özel bir etki alanında, yani XSLT dilinde ve destekleyici API'lerde uzmanlık gerektirir.  
  
 LINQ'dan XML'e, saf işlevsel dönüşümleri C# veya Visual Basic kodu içinde anlamlı ve güçlü bir şekilde kodlamak için gerekli araçları sağlar. Örneğin, LINQ-XML belgelerindeki örneklerin çoğu saf işlevsel bir yaklaşım kullanır. Ayrıca, [Öğretici: Bir WordprocessingML Belgesinde (C#) öğreticide İçeriği manipüle](./shape-of-wordprocessingml-documents.md) etmede, Bir Microsoft Word belgesindeki bilgileri işlemek için işlevsel bir yaklaşımla LINQ'dan XML'ye kadar kullanırız.  
  
 Linq ile XML'in diğer Microsoft XML teknolojileri ile daha eksiksiz bir karşılaştırması için LINQ ile [XML ile Diğer XML Teknolojileri'ne](./linq-to-xml-vs-other-xml-technologies.md)bakın.  
  
XSLT, kaynak belgedüzensiz bir yapıya sahipolduğunda belge merkezli dönüşümler için önerilen araçtır. Ancak, LINQ xml de belge merkezli dönüşümler gerçekleştirebilirsiniz. Daha fazla bilgi için, [LINQ'u XSLT stilinde (C#) XML ağaçlarına dönüştürmek için ek açıklamaları nasıl kullanacağız'ı](./how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md)görün.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf İşlevsel Dönüşümlere Giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)](./shape-of-wordprocessingml-documents.md)
- [LINQ ve XML ve Diğer XML Teknolojileri](./linq-to-xml-vs-other-xml-technologies.md)
