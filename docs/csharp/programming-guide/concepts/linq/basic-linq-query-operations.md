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
ms.openlocfilehash: b8884f2ae230a92f48e93d9b5408ff241f874f92
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968198"
---
# <a name="basic-linq-query-operations-c"></a>Temel LINQ Sorgu İşlemleri (C#)
Bu konu, kısa bir giriş sağlar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri ve bazı sorguda gerçekleştirdiğiniz işlemleri tipik türleri. Aşağıdaki konularda daha ayrıntılı bilgi verilmiştir:  
  
 [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [İzlenecek yol: Sorguları yazmaC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  Zaten bir sorgu dili SQL veya XQuery gibi alışık olduğunuz, bu konunun en atlayabilirsiniz. Hakkında bilgi edinin "`from` yan tümcesi" yan tümcelerinde sırası hakkında bilgi edinmek için sonraki bölümde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde.  
  
## <a name="obtaining-a-data-source"></a>Bir Veri Kaynağı Elde Etme  
 İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, ilk adımıdır veri kaynağını belirtmek için. Kullanmadan önce C# çoğu programlama dilinden olduğu gibi bir değişkeni bildirilmelidir. İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu `from` yan tümcesi gelen ilk veri kaynağı sunmak için (`customers`) ve *aralık değişkeni* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Yineleme değişkeni aralık değişkeni benzer bir `foreach` dışında bir sorgu ifadesinde gerçek yineleme gerçekleşir, döngü. Sorgu yürütüldüğünde, aralık değişkeni art arda gelen her öğe için bir başvuru olarak hizmet verecektir `customers`. Derleyicinin türü çıkarsayabilir `cust`, açıkça belirtmeniz gerekmez. Ek aralık değişkenleri sunulan tarafından bir `let` yan tümcesi. Daha fazla bilgi için [let yan tümcesi](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  Genel olmayan veri kaynakları gibi <xref:System.Collections.ArrayList>, Aralık değişkeninin türü açıkça belirtilmelidir. Daha fazla bilgi için [nasıl yapılır: LINQ ile ArrayList sorgulama (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) ve [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtreleme  
 Bir Boolean ifadesinin biçiminde bir filtre uygulamak için en yaygın sorgu işlemi olabilir. Filtre ifadesi doğru öğeleri döndürmek için sorguyu neden olur. Kullanarak bir sonuç getirdi `where` yan tümcesi. Filtre, geçerli kaynak sırasından çıkarılacak öğeleri belirtir. Aşağıdaki örnekte, yalnızca `customers` Londra bir adrese sahip döndürülür.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Tanıdık C# mantıksal kullanabilirsiniz `AND` ve `OR` gibi birçok gerekli olduğu gibi ifadeler filtre uygulamak için işleçleri `where` yan tümcesi. Örneğin, yalnızca müşterilerin "Londra'dan" döndürülecek `AND` adı olan "aşağıdaki kodu yazdığınız Devon":  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Müşteriler Londra veya Paris döndürmek için aşağıdaki kodu yazabilirsiniz:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Daha fazla bilgi için [burada yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Sıralama  
 Genellikle döndürülen verileri sıralamak uygundur. `orderby` Yan tümcesi neden öğeleri döndürülen dizideki sıralanan türü için varsayılan karşılaştırıcı göre sıralanacak. Örneğin, aşağıdaki sorguyu göre sonuçları sıralamak için Genişletilebilir `Name` özelliği. Çünkü `Name` bir dize ise varsayılan karşılaştırıcı bir alfabetik sıralama A'dan Z'ye gerçekleştirir.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Sonuçları Z'den A'ya, ters sırada sıralamak için kullanmak `orderby…descending` yan tümcesi.  
  
 Daha fazla bilgi için [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Gruplandırma  
 `group` Yan tümcesi, belirttiğiniz bir anahtarına göre sonuçlarınızı Grup olanak sağlar. Örneğin sonuçların göre gruplanmış belirtebilirsiniz `City` Londra veya Paris tüm müşterilerden tek tek gruplar içinde olacak şekilde. Bu durumda, `cust.City` anahtardır.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Son ne zaman bir sorgu ile bir `group` yan tümcesi, sonuçlarınızı bir liste biçiminde alın. Listedeki her öğe olan bir nesnedir bir `Key` üye ve bu anahtarın altında gruplanmış öğelerin listesi. Grupları bir dizi üreten bir bir sorgu üzerinde gezinmek, iç içe bir kullanmalısınız `foreach` döngü. Dış döngü her bir grup üzerinde yinelenir ve iç döngü her grubun üyeleri üzerinde yinelenir.  
  
 Grup işlemi sonuçlarını başvurmalıdır, kullanabileceğiniz `into` daha da sorgulanabilir bir tanımlayıcı oluşturmak için anahtar sözcüğü. Aşağıdaki sorgu, ikiden fazla müşteriler içeren gruplar döndürür:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Daha fazla bilgi için [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Katılma  
 Birleştirme işlemleri oluşturma dizileri arasında ilişkiler, veri kaynakları, açıkça modellenmez. Örneğin, tüm müşteriler ve aynı konumda olan dağıtımcıların bulmak için bir birleştirme gerçekleştirebilirsiniz. İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` yan tümcesi her zaman çalışır nesne koleksiyonları veritabanı tabloları yerine karşı doğrudan.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kullanmak zorunda değil `join` SQL'de çünkü bunu sıklıkta yabancı anahtarları [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesne modelinde öğelerin bir koleksiyonunu tutan özellikleri olarak temsil edilir. Örneğin, bir `Customer` nesneyi içeren koleksiyonu `Order` nesneleri. Birleşim gerçekleştirme yerine nokta gösterimi kullanılarak siparişleri erişin:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Daha fazla bilgi için [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Seçme (Tahminler)  
 `select` Yan tümcesi sorgusunun sonuçları üretir ve "şekline" ya da her döndürülen öğe türünü belirtir. Örneğin, sizin sonuçlarınız, tam oluşacağını belirtebilirsiniz `Customer` nesneler, yalnızca bir üye, üyelerin bir alt kümesini veya tamamen farklı sonuç tür dayalı bir hesaplama veya yeni nesne oluşturma. Zaman `select` yan tümcesi bir kopyasını bir kaynak öğesi dışında bir şey üretir, işlem çağrılır bir *projeksiyon*. Projeksiyonlar verileri dönüştürmek için kullanımı, güçlü bir özellik mi [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde. Daha fazla bilgi için [LINQ (C#) ile veri dönüştürmeler](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) ve [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [İzlenecek yol: Sorguları yazmaC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Query Keywords (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)
- [Anonim Tipler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
