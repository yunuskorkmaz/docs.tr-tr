---
title: Temel LINQ Sorgu İşlemleri (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 91c038303c1ad7c2530964d3102aae49090c4c2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635945"
---
# <a name="basic-linq-query-operations-c"></a>Temel LINQ Sorgu İşlemleri (C#)
Bu konu, LINQ sorgu ifadelerine ve bir sorguda gerçekleştirdiğiniz tipik işlem türlerinden bazılarına kısa bir giriş sağlar. Daha ayrıntılı bilgi aşağıdaki konularda:  
  
 [LINQ Sorgu İfadeleri](../../../linq/index.md)  
  
 [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)  
  
 [Walkthrough: C'de Sorgu Yazma #](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> SQL veya XQuery gibi bir sorgu dilini zaten biliyorsanız, bu konunun çoğunu atlayabilirsiniz. LINQ sorgu`from` ifadelerindeki yan tümcelerin sırası hakkında bilgi edinmek için bir sonraki bölümdeki "yan tümce" hakkında bilgi edinin.  
  
## <a name="obtaining-a-data-source"></a>Bir Veri Kaynağı Elde Etme  
 LINQ sorgusunda ilk adım veri kaynağını belirtmektir. Çoğu programlama dilinde olduğu gibi C#'da da kullanılmadan önce bir değişken in bildirilmesi gerekir. BIR LINQ `from` sorgusunda, yan tümce önce veri`customers`kaynağını ( )`cust`ve aralık *değişkenini* ( ) tanıtmak için gelir.  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Aralık değişkeni, sorgu ifadesinde gerçek `foreach` yineleme olmaması dışında bir döngüdeki yineleme değişkeni gibidir. Sorgu yürütüldüğünde, aralık değişkeni `customers`' deki her ardışık öğeye başvuru görevi göreceksiniz. Derleyici türünü `cust`çıkarabileceğinden, bunu açıkça belirtmeniz gerekmez. Ek aralık değişkenleri bir `let` yan tümce ile tanıtılabilir. Daha fazla bilgi için [bkz.](../../../language-reference/keywords/let-clause.md)  
  
> [!NOTE]
> Gibi genel olmayan veri <xref:System.Collections.ArrayList>kaynakları için, aralık değişkeni açıkça yazılmalıdır. Daha fazla bilgi için LINQ (C#) ile ve [yan tümcesinden](../../../language-reference/keywords/from-clause.md) [bir ArrayList'i nasıl sorgularız](./how-to-query-an-arraylist-with-linq.md) bilgi sini görün.  
  
## <a name="filtering"></a>Filtreleme  
 Muhtemelen en yaygın sorgu işlemi Boolean ifadesi şeklinde bir filtre uygulamaktır. Filtre, sorgunun yalnızca ifadenin doğru olduğu öğeleri döndürmesine neden olur. `where` Sonuç, yan tümce kullanılarak elde edilir. Etkin filtre, kaynak dizisinden hangi öğelerin dışlanacağı belirtilir. Aşağıdaki örnekte, yalnızca `customers` Londra'da adresi olanlar iade edilir.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Yan tümcede gerektiği `AND` kadar `OR` filtre ifadesi uygulamak için tanıdık C# mantıksal ve işleçleri kullanabilirsiniz. `where` Örneğin, yalnızca "Londra"dan adı `AND` "Devon" olan müşterileri iade etmek için aşağıdaki kodu yazarsınız:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Londra veya Paris'ten gelen müşterileri iade etmek için aşağıdaki kodu yazarsınız:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Daha fazla bilgi için [bkz.](../../../language-reference/keywords/where-clause.md)  
  
## <a name="ordering"></a>Sıralama  
 Genellikle döndürülen verileri sıralamak için uygundur. Yan `orderby` tümce, döndürülen sırada yer alan öğelerin sıralanan tür için varsayılan karşılayıcıya göre sıralansın. Örneğin, aşağıdaki sorgu `Name` özelliğine göre sonuçları sıralamak için genişletilebilir. Bir `Name` dize olduğundan, varsayılan karşılayıcı A'dan Z'ye alfabetik bir sıralama gerçekleştirir.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Sonuçları z'den A'ya ters sırayla `orderby…descending` sıralamak için yan tümceyi kullanın.  
  
 Daha fazla bilgi için [orderby yan tümcesi'ne](../../../language-reference/keywords/orderby-clause.md)bakın.  
  
## <a name="grouping"></a>Gruplandırma  
 Yan `group` tümce, sonuçlarınızı belirttiğiniz bir anahtara göre gruplandırmanızı sağlar. Örneğin, Londra veya Paris'ten gelen tüm `City` müşterilerin ayrı gruplar halinde olması için sonuçların bunlara göre gruplandırılması gerektiğini belirtebilirsiniz. Bu durumda, `cust.City` anahtardır.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Bir sorguyu bir `group` yan tümceyle sonladiğinizde, sonuçlarınız liste listesi biçiminde dir. Listedeki her öğe, bir `Key` üyesi ve bu anahtar altında gruplanmış öğelerin listesi olan bir nesnedir. Bir grup dizisi oluşturan bir sorgu üzerinde yinelediğinizde, iç `foreach` içe bir döngü kullanmanız gerekir. Dış döngü her grubun üzerinde yineler ve iç döngü her grubun üyeleri üzerinde yineler.  
  
 Bir grup işleminin sonuçlarına başvurmanız gerekiyorsa, `into` daha fazla sorgulanabilecek bir tanımlayıcı oluşturmak için anahtar sözcüğü kullanabilirsiniz. Aşağıdaki sorgu yalnızca ikiden fazla müşteri içeren grupları döndürür:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Daha fazla bilgi için [grup yan tümcesi'ne](../../../language-reference/keywords/group-clause.md)bakın.  
  
## <a name="joining"></a>Katma  
 Birleştirme işlemleri, veri kaynaklarında açıkça modellenmemiş diziler arasında ilişki oluşturur. Örneğin, aynı konuma sahip tüm müşterileri ve distribütörleri bulmak için bir birleştirme gerçekleştirebilirsiniz. LINQ'da `join` yan tümce her zaman veritabanı tabloları yerine nesne koleksiyonlarına karşı çalışır.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 LINQ'da, SQL'de `join` kullandığınız sıklıkta kullanmanız gerekmez, çünkü LINQ'daki yabancı anahtarlar nesne modelinde bir öğe koleksiyonu tutan özellikler olarak temsil edilir. Örneğin, bir `Customer` nesne nesnelerin `Order` bir koleksiyon içerir. Birleştirme gerçekleştirmek yerine, nokta gösterimi kullanarak siparişlere erişebilirsiniz:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Daha fazla bilgi için [ara yan tümcesi'ne](../../../language-reference/keywords/join-clause.md)bakın.  
  
## <a name="selecting-projections"></a>Seçme (Tahminler)  
 Yan `select` tümce sorgunun sonuçlarını üretir ve döndürülen her öğenin "şeklini" veya türünü belirtir. Örneğin, sonuçlarınızın tam `Customer` nesnelerden mi, yalnızca bir üyeden, bir üye alt kümesinden mi yoksa bir hesaplamaya veya yeni nesne oluşturmaya dayalı tamamen farklı bir sonuç türünden mi oluşacağını belirtebilirsiniz. `select` Yan tümce kaynak öğenin bir kopyası ndan başka bir şey ürettiğinde, işlem *projeksiyon*olarak adlandırılır. Verileri dönüştürmek için projeksiyonların kullanılması LINQ sorgu ifadelerinin güçlü bir yeteneğidir. Daha fazla bilgi için [LINQ (C#) ile Veri Dönüşümleri](./data-transformations-with-linq.md) ve [select yan tümcesi](../../../language-reference/keywords/select-clause.md)'ne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ Sorgu İfadeleri](../../../linq/index.md)
- [Walkthrough: C'de Sorgu Yazma #](./walkthrough-writing-queries-linq.md)
- [Sorgu Anahtar Kelimeleri (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Anonim Türler](../../classes-and-structs/anonymous-types.md)
