---
title: İşlevsel ve yordamsal programlama
description: LINQ to XML, XML uygulamaları oluşturmak için hem işlevsel oluşturma hem de yordamsal teknikleri destekler. İşlevsel oluşturma, bildirime dayalı bir yaklaşımdır. Yordamsal teknikler, XML ağaçlarının bellek içi değişikliğini destekler.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: a2753a31e88fd338dad61063f559431869b9e17f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552997"
---
# <a name="functional-vs-procedural-programming-linq-to-xml"></a>İşlevsel ve yordamsal programlama (LINQ to XML)

Çeşitli türlerdeki XML uygulamaları vardır:

- Bazı uygulamalar kaynak XML belgelerini alır ve kaynak belgelerden farklı bir şekilde yeni XML belgeleri oluşturur.
- Bazı uygulamalar kaynak XML belgelerini alır ve sonuç belgelerini HTML veya CSV metin dosyaları gibi tamamen farklı bir biçimde oluşturur.
- Bazı uygulamalar kaynak XML belgelerini alır ve bir veritabanına kayıt ekler.
- Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri alır ve bundan XML belgesi oluşturur.

Bunlar, XML uygulaması türlerinin hepsi değildir, ancak bunlar bir XML Programlayıcısının uygulamak zorunda olduğu işlevsellik türlerinin temsili bir kümesidir.

Bu tür uygulamaların tümünde, bir geliştiricinin uygulayabileceğiniz iki yaklaşım vardır:

- Bildirim temelli bir yaklaşım kullanılarak işlevsel oluşturma.
- Yordamsal kodu kullanarak bellek içi XML ağacı değişikliği.

LINQ to XML her iki yaklaşımı destekler.

İşlevsel yaklaşımı kullanırken, kaynak belgeleri alan ve istenen şekle sahip tamamen yeni sonuç belgeleri oluşturan dönüşümler yazarsınız.

Bir XML ağacını yerinde değiştirirken, düğüm içi bir XML ağacındaki düğümlerde geçen ve gezinen, düğümleri ekleme, silme ve değiştirme gibi bir kod yazın.

LINQ to XML iki yaklaşımla de kullanabilirsiniz. Aynı sınıfları ve bazı durumlarda aynı yöntemleri kullanırsınız. Ancak, iki yaklaşımın yapısı ve amaçları farklıdır. Örneğin, farklı durumlarda, bir veya diğer yaklaşım genellikle daha iyi performansa sahip olur ve daha fazla veya daha az bellek kullanır. Buna ek olarak, bir veya başka bir yaklaşım daha fazla erişilebilir kod yazmak ve sağlamak daha kolay olacaktır.

Bu iki yaklaşımı görmek için bkz. [bellek ıçı XML ağacı değişikliği ve işlevsel oluşturma](in-memory-xml-tree-modification-vs-functional-construction.md).

İşlev dönüşümleri yazma hakkında bir öğretici için bkz. [saf işlevsel dönüşümlere giriş](introduction-pure-functional-transformations.md).
