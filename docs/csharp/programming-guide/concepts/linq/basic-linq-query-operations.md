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
ms.openlocfilehash: 361101258caca763502f92d897866c75bc8d7da2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418718"
---
# <a name="basic-linq-query-operations-c"></a>Temel LINQ Sorgu İşlemleri (C#)
Bu konu, sorgu ifadelerine [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] için kısa bir giriş ve bir sorguda gerçekleştirdiğiniz bazı tipik işlem türlerinden bazılarını vermektedir. Daha ayrıntılı bilgi aşağıdaki konularda yer verilmiştir:  
  
 [LINQ sorgu Ifadeleri](../../../linq/index.md)  
  
 [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)  
  
 [İzlenecek yol: sorguları yazmaC#](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> SQL veya XQuery gibi bir sorgu dili zaten hakkında bilginiz varsa, bu konunun çoğunu atlayabilirsiniz. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde yan tümceler sırası hakkında bilgi edinmek için sonraki bölümde "`from` yan tümcesi" konusunu okuyun.  
  
## <a name="obtaining-a-data-source"></a>Bir Veri Kaynağı Elde Etme  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusunda ilk adım veri kaynağını belirtmektir. Çoğu C# programlama dilinde olduğu gibi, kullanılmadan önce bir değişken bildirilmelidir. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusunda, veri kaynağını (`customers`) ve *Aralık değişkenini* (`cust`) tanıtmak için ilk olarak `from` yan tümcesi gelir.  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Aralık değişkeni, bir sorgu ifadesinde hiçbir gerçek yineleme gerçekleşmedikçe, bir `foreach` döngüsünde yineleme değişkeni gibidir. Sorgu yürütüldüğünde, Aralık değişkeni `customers`art arda her bir öğeye başvuru olarak görev yapar. Derleyici `cust`türünü çıkarsanbildiğinden, açıkça belirtmeniz gerekmez. Ek Aralık değişkenleri, bir `let` yan tümcesi tarafından tanıtılamaz. Daha fazla bilgi için bkz. [Let yan tümcesi](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> <xref:System.Collections.ArrayList>gibi genel olmayan veri kaynakları için, Aralık değişkeni açıkça yazılmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: bir ArrayList 'i LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) ve [from yan tümcesi](../../../language-reference/keywords/from-clause.md)ile sorgulama.  
  
## <a name="filtering"></a>Filtreleme  
 Büyük olasılıkla en yaygın sorgu işlemi, bir filtrenin Boole ifadesi biçiminde uygulanmasından kaynaklanıyor olabilir. Filtre sorgunun yalnızca ifadenin true olduğu öğeleri döndürmesine neden olur. Sonuç, `where` yan tümcesi kullanılarak oluşturulur. Etkin filtre, kaynak sırasından hangi öğelerin dışlanacağını belirtir. Aşağıdaki örnekte, yalnızca Londra 'da bir adrese sahip olan `customers` döndürülür.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Tanıdık C# mantıksal `AND` ve `OR` işleçlerini `where` yan tümcesinde gereken sayıda filtre ifadesi uygulamak için kullanabilirsiniz. Örneğin, yalnızca "Istanbul" `AND`, adı "Devon" olan müşterileri döndürmek için aşağıdaki kodu yazarsınız:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Londra veya Paris 'ten müşterileri döndürmek için aşağıdaki kodu yazarsınız:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Sıralama  
 Genellikle döndürülen verileri sıralamak uygundur. `orderby` yan tümcesi, döndürülen dizideki öğelerin sıralanmakta olan türün varsayılan karşılaştırmasına göre sıralanmasına neden olur. Örneğin, aşağıdaki sorgu, `Name` özelliğine göre sonuçları sıralamak için genişletilebilir. `Name` bir dize olduğundan, varsayılan karşılaştırıcı, A 'dan Z 'ye alfabetik bir sıralama gerçekleştirir.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Sonuçları Z 'den A 'ya doğru sırada sıralamak için `orderby…descending` yan tümcesini kullanın.  
  
 Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Gruplandırma  
 `group` yan tümcesi, sonuçlarınızı belirttiğiniz bir anahtara göre gruplandırmanızı sağlar. Örneğin, Londra veya Paris 'teki tüm müşterilerin ayrı gruplar halinde olması için sonuçların `City` göre gruplanmasını belirtebilirsiniz. Bu durumda, `cust.City` anahtardır.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Bir `group` yan tümcesiyle bir sorgu sonlandırdığınızda, sonuçlarınız bir liste listesi biçimini alır. Listedeki her öğe, bir `Key` üyesine ve bu anahtar altında gruplanmış öğelerin listesine sahip olan bir nesnedir. Bir grup dizisi üreten bir sorgu üzerinde yineleme yaparken, iç içe geçmiş bir `foreach` döngüsü kullanmanız gerekir. Dış döngü her grup üzerinde yinelenir ve iç döngü her bir grubun üyesi üzerinde yinelenir.  
  
 Bir grup işleminin sonuçlarına başvurmanız gerekirse, daha fazla sorgulanabilecek bir tanımlayıcı oluşturmak için `into` anahtar sözcüğünü kullanabilirsiniz. Aşağıdaki sorgu yalnızca ikiden fazla müşteri içeren grupları döndürür:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Daha fazla bilgi için bkz. [Group yan tümcesi](../../../language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Katılma  
 JOIN işlemleri, veri kaynaklarında açıkça Modellenmemiş diziler arasında ilişkiler oluşturur. Örneğin, aynı konuma sahip tüm müşterileri ve dağıtımcıları bulmak için bir JOIN işlemi gerçekleştirebilirsiniz. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` yan tümcesi her zaman doğrudan veritabanı tabloları yerine nesne koleksiyonlarına göre geçerlidir.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yabancı anahtarları nesne modelinde bir öğe koleksiyonu tutan özellikler olarak temsil ettiğinden, SQL 'de yaptığınız gibi `join` kullanmak zorunda değilsiniz. Örneğin, bir `Customer` nesnesi bir `Order` nesneleri koleksiyonu içerir. Bir JOIN gerçekleştirmek yerine, siparişe nokta gösterimini kullanarak erişirsiniz:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Seçme (Tahminler)  
 `select` yan tümcesi sorgunun sonuçlarını üretir ve döndürülen her öğenin "şeklini" veya türünü belirtir. Örneğin, sonuçlarınızın tam `Customer` nesneleri, yalnızca bir üye, bir üye alt kümesi veya bir hesaplama ya da yeni nesne oluşturmaya göre tamamen farklı sonuç türü olacağını belirtebilirsiniz. `select` yan tümcesi kaynak öğenin bir kopyası dışında bir şey üretirse, işleme bir *projeksiyon*olarak adlandırılır. Verileri dönüştürmek için projeksiyonun kullanımı, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinin güçlü bir özelliğidir. Daha fazla bilgi için bkz. [LINQ (C#)](./data-transformations-with-linq.md) ve [Select yan tümcesiyle](../../../language-reference/keywords/select-clause.md)veri dönüştürmeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ sorgu Ifadeleri](../../../linq/index.md)
- [İzlenecek yol: sorguları yazmaC#](./walkthrough-writing-queries-linq.md)
- [Sorgu anahtar sözcükleri (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Anonim Tipler](../../classes-and-structs/anonymous-types.md)
