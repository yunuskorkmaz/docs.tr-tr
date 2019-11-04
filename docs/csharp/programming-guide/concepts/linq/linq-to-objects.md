---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 8c0eb71fffdd29d9599d74c789a66ec7caf1faeb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418172"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
"LINQ to Objects" terimi, bir ara LINQ sağlayıcısının veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](./linq-to-xml-overview.md)gibi API kullanılmadan doğrudan herhangi bir <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> koleksiyonuyla LINQ sorgularının kullanımını ifade eder. <xref:System.Collections.Generic.List%601>, <xref:System.Array>veya <xref:System.Collections.Generic.Dictionary%602>gibi herhangi bir sıralanabilir koleksiyonu sorgulamak için LINQ 'i kullanabilirsiniz. Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET Framework API 'SI tarafından döndürülen olabilir.  
  
 Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder. Eski şekilde, bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık `foreach` döngüleri yazmanız gerekiyordu. LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.  
  
 Ayrıca, LINQ sorguları geleneksel `foreach` döngülerine göre üç temel avantaj sunar:  
  
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
  
 [Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama](./how-to-query-an-arraylist-with-linq.md)  
 İçinde C#ArrayList 'in nasıl sorgulanacağını gösterir.  
  
 [Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 <xref:System.Collections.Generic.IEnumerable%601> arabirimine uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar.  
  
 [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)  
 LINQ ' i açıklayan ve sorguları gerçekleştiren koda örnek sağlayan konulara bağlantılar sağlar.
