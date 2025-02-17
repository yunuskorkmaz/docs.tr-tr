---
title: LINQ to Objects (C#)
description: <T>Bir ara LINQ sağlayıcısı veya API olmadan herhangi bir IEnumerable veya IEnumerable KOLEKSIYONUYLA LINQ sorguları kullanan C# ' de LINQ to Objects hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 575708f14487670a4371d470dcdcf650b03c3175
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202532"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)

"LINQ to Objects" terimi, <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> bır ara LINQ sağlayıcısı veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](../../../../standard/linq/linq-xml-overview.md)gibi API KULLANıLMADAN doğrudan herhangi bir veya koleksiyonuyla LINQ sorgularının kullanımını ifade eder. , Veya gibi tüm sıralanabilir koleksiyonları sorgulamak için LINQ kullanabilirsiniz <xref:System.Collections.Generic.List%601> <xref:System.Array> <xref:System.Collections.Generic.Dictionary%602> . Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET API 'SI tarafından döndürülebilir.  
  
 Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder. Eski şekilde, `foreach` bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık döngüler yazmanız gerekiyordu. LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.  
  
 Ayrıca, LINQ sorguları geleneksel Döngülerde üç temel avantaj sunar `foreach` :  
  
- Özellikle birden fazla koşula filtre uygulanırken bunlar daha kısa ve okunabilir.  
  
- En az uygulama kodu ile güçlü filtreleme, sıralama ve gruplama özellikleri sağlar.  
  
- Bunlar, çok az değişiklik yapmadan diğer veri kaynaklarına da eklenebilir.  
  
 Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem daha karmaşıktır, geleneksel yineleme teknikleri yerine LINQ kullanarak bunu daha fazla avantaj elde edersiniz.  
  
 Bu bölümün amacı, bazı Select örnekleri ile LINQ yaklaşımını göstermektir. Bu, kapsamlı olmak üzere tasarlanmamıştır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [LINQ ve dizeler (C#)](./linq-and-strings.md)  
 LINQ 'in dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu ilkeleri gösteren makalelerin bağlantılarını içerir.  
  
 [LINQ ve yansıma (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 LINQ 'in yansıma kullanımını gösteren bir örneğe bağlantılar.  
  
 [LINQ ve dosya dizinleri (C#)](./linq-and-file-directories.md)  
 LINQ 'in dosya sistemleriyle etkileşime geçmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu kavramları gösteren makalelerin bağlantılarını içerir.  
  
 [LINQ ile ArrayList 'i sorgulama (C#)](./how-to-query-an-arraylist-with-linq.md)  
 C# içinde ArrayList 'in nasıl sorgulanacağını gösterir.  
  
 [LINQ sorguları için özel yöntemler ekleme (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar <xref:System.Collections.Generic.IEnumerable%601> .  
  
 [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)  
 LINQ ' i açıklayan ve sorgu gerçekleştiren koda örnek sağlayan makalelere bağlantılar sağlar.
