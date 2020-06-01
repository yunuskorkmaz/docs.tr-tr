---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: c488e49283f3e30ea729adf111fd9ca297039838
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241571"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
"LINQ to Objects" terimi, <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> bır ara LINQ sağlayıcısı veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](./linq-to-xml-overview.md)gibi API KULLANıLMADAN doğrudan herhangi bir veya koleksiyonuyla LINQ sorgularının kullanımını ifade eder. , Veya gibi tüm sıralanabilir koleksiyonları sorgulamak için LINQ kullanabilirsiniz <xref:System.Collections.Generic.List%601> <xref:System.Array> <xref:System.Collections.Generic.Dictionary%602> . Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET API 'SI tarafından döndürülebilir.  
  
 Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder. Eski şekilde, `foreach` bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık döngüler yazmanız gerekiyordu. LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.  
  
 Ayrıca, LINQ sorguları geleneksel Döngülerde üç temel avantaj sunar `foreach` :  
  
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
 Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar <xref:System.Collections.Generic.IEnumerable%601> .  
  
 [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)  
 LINQ ' i açıklayan ve sorguları gerçekleştiren koda örnek sağlayan konulara bağlantılar sağlar.
