---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344777"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
"LINQ to Objects" terimi, bir ara LINQ sağlayıcısı veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](./linq-to-xml-overview.md)gibi <xref:System.Collections.IEnumerable> API <xref:System.Collections.Generic.IEnumerable%601> kullanılmadan doğrudan herhangi bir veya koleksiyonuyla LINQ sorgularının kullanımını ifade eder. , <xref:System.Collections.Generic.List%601> <xref:System.Array>Veya <xref:System.Collections.Generic.Dictionary%602>gibi tüm sıralanabilir koleksiyonları sorgulamak için LINQ kullanabilirsiniz. Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET Framework API 'SI tarafından döndürülen olabilir.  
  
 Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder. Eski şekilde, bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık `foreach` döngüler yazmanız gerekiyordu. LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.  
  
 Ayrıca, LINQ sorguları geleneksel `foreach` Döngülerde üç temel avantaj sunar:  
  
1. Özellikle birden fazla koşula filtre uygulanırken bunlar daha kısa ve okunabilir.  
  
2. En az uygulama kodu ile güçlü filtreleme, sıralama ve gruplama özellikleri sağlar.  
  
3. Bunlar, çok az değişiklik yapmadan diğer veri kaynaklarına da eklenebilir.  
  
 Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem daha karmaşıktır, geleneksel yineleme teknikleri yerine LINQ kullanarak bunu daha fazla avantaj elde edersiniz.  
  
 Bu bölümün amacı, bazı Select örnekleri ile LINQ yaklaşımını göstermektir. Bu, kapsamlı olmak üzere tasarlanmamıştır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [LINQ ve dizeler (C#)](./linq-and-strings.md)  
 LINQ 'in dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu ilkeleri gösteren konuların bağlantılarını içerir.  
  
 [LINQ ve yansıma (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 LINQ 'in yansıma kullanımını gösteren bir örneğe bağlantılar.  
  
 [LINQ ve dosya dizinleri (C#)](./linq-and-file-directories.md)  
 LINQ 'in dosya sistemleriyle etkileşime geçmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu kavramları gösteren konuların bağlantılarını içerir.  
  
 [LINQ ile ArrayList 'i sorgulama (C#)](./how-to-query-an-arraylist-with-linq.md)  
 C# içinde ArrayList 'in nasıl sorgulanacağını gösterir.  
  
 [LINQ sorguları için özel yöntemler ekleme (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 <xref:System.Collections.Generic.IEnumerable%601> Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar.  
  
 [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)  
 LINQ ' i açıklayan ve sorguları gerçekleştiren koda örnek sağlayan konulara bağlantılar sağlar.
