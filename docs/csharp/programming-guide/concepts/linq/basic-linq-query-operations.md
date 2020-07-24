---
title: Temel LINQ Sorgu İşlemleri (C#)
description: LINQ sorgu ifadelerine ve bir sorguda gerçekleştirebileceğiniz işlemlerden bazılarını tanıtın.
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
ms.openlocfilehash: d9653be8b67ef4d971c157b8dd8d82b2ae3c2287
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105531"
---
# <a name="basic-linq-query-operations-c"></a>Temel LINQ Sorgu İşlemleri (C#)
Bu konu, LINQ sorgu ifadelerine kısa bir giriş ve bir sorguda gerçekleştirdiğiniz bazı tipik işlem türlerinden bazılarını vermektedir. Daha ayrıntılı bilgi aşağıdaki konularda yer verilmiştir:  
  
 [LINQ sorgu Ifadeleri](../../../linq/index.md)  
  
 [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md)  
  
 [İzlenecek yol: C 'de sorgu yazma #](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> SQL veya XQuery gibi bir sorgu dili zaten hakkında bilginiz varsa, bu konunun çoğunu atlayabilirsiniz. `from`LINQ sorgu ifadelerinde yan tümceler sırası hakkında bilgi edinmek için sonraki bölümde "yan tümce" konusunu okuyun.  
  
## <a name="obtaining-a-data-source"></a>Bir Veri Kaynağı Elde Etme  
 Bir LINQ sorgusunda, ilk adım veri kaynağını belirtmektir. C# ' ta çoğu programlama dilinde, bir değişken kullanılmadan önce bildirilmelidir. LINQ sorgusunda, `from` yan tümce ilk olarak veri kaynağını ( `customers` ) ve *Aralık değişkenini* () tanıtmak için gelir `cust` .  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Aralık değişkeni, bir `foreach` sorgu ifadesinde gerçek yineleme gerçekleşmediğinde, döngü içindeki yineleme değişkenine benzer. Sorgu yürütüldüğünde, Aralık değişkeni içindeki her bir ardışık öğeye başvuru olarak görev yapar `customers` . Derleyici türünü çıkarsanbildiğinden `cust` , açıkça belirtmeniz gerekmez. Ek Aralık değişkenleri bir yan tümce tarafından bulunabilir `let` . Daha fazla bilgi için bkz. [Let yan tümcesi](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> Gibi genel olmayan veri kaynakları için <xref:System.Collections.ArrayList> , Aralık değişkeni açıkça yazılmalıdır. Daha fazla bilgi için bkz. [LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) ve [from yan tümcesi](../../../language-reference/keywords/from-clause.md)ile ArrayList 'i sorgulama.  
  
## <a name="filtering"></a>Filtreleme  
 Büyük olasılıkla en yaygın sorgu işlemi, bir filtrenin Boole ifadesi biçiminde uygulanmasından kaynaklanıyor olabilir. Filtre sorgunun yalnızca ifadenin true olduğu öğeleri döndürmesine neden olur. Sonuç, `where` yan tümcesi kullanılarak oluşturulur. Etkin filtre, kaynak sırasından hangi öğelerin dışlanacağını belirtir. Aşağıdaki örnekte, yalnızca `customers` Londra 'da bir adresi olan kişiler döndürülür.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 `AND` `OR` Tümce içinde gereken sayıda filtre ifadesi uygulamak Için tanıdık C# mantıksal ve işleçlerini kullanabilirsiniz `where` . Örneğin, yalnızca adı "Devon" olan "Londra" dan müşterileri döndürmek için `AND` aşağıdaki kodu yazarsınız:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Londra veya Paris 'ten müşterileri döndürmek için aşağıdaki kodu yazarsınız:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Sıralama  
 Genellikle döndürülen verileri sıralamak uygundur. `orderby`Yan tümcesi, döndürülen dizideki öğelerin sıralanmakta olan türün varsayılan karşılaştırmasına göre sıralanmasına neden olur. Örneğin, aşağıdaki sorgu sonuçları özelliği temel alarak sıralamak için Genişletilebilir `Name` . `Name`Bir dize olduğundan, varsayılan karşılaştırıcı, a 'Dan Z 'ye alfabetik bir sıralama gerçekleştirir.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Sonuçları Z 'den A 'ya doğru sırada sıralamak için `orderby…descending` yan tümcesini kullanın.  
  
 Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Gruplandırma  
 `group`Yan tümcesi, sonuçlarınızı belirttiğiniz bir anahtara göre gruplandırmanızı sağlar. Örneğin, `City` Londra veya Paris 'teki tüm müşterilerin ayrı gruplar halinde olması için sonuçların tarafından gruplanmasını belirtebilirsiniz. Bu durumda, `cust.City` anahtardır.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Bir yan tümcesiyle bir sorgu sonlandırdığınızda `group` , sonuçlarınız bir liste listesi alır. Listedeki her öğe, bir `Key` üyeye ve bu anahtar altında gruplanmış bir öğe listesine sahip olan bir nesnedir. Grup dizisi üreten bir sorgu üzerinde yineleme yaparken, iç içe geçmiş bir döngü kullanmanız gerekir `foreach` . Dış döngü her grup üzerinde yinelenir ve iç döngü her bir grubun üyesi üzerinde yinelenir.  
  
 Bir grup işleminin sonuçlarına başvurmanız gerekirse, `into` daha fazla sorgulanabilecek bir tanımlayıcı oluşturmak için anahtar sözcüğünü kullanabilirsiniz. Aşağıdaki sorgu yalnızca ikiden fazla müşteri içeren grupları döndürür:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Daha fazla bilgi için bkz. [Group yan tümcesi](../../../language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Katma  
 JOIN işlemleri, veri kaynaklarında açıkça Modellenmemiş diziler arasında ilişkiler oluşturur. Örneğin, aynı konuma sahip tüm müşterileri ve dağıtımcıları bulmak için bir JOIN işlemi gerçekleştirebilirsiniz. LINQ içinde `join` yan tümce her zaman veritabanı tabloları yerine yalnızca nesne koleksiyonlarına göre geçerlidir.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 LINQ ' ta, LINQ `join` içindeki yabancı anahtarlar nesne modelinde bir öğe koleksiyonu tutan özellikler olarak temsil edildiği IÇIN SQL 'de yaptığınız kadar sık kullanmanız gerekmez. Örneğin, bir `Customer` nesnesi bir nesne koleksiyonu içerir `Order` . Bir JOIN gerçekleştirmek yerine, siparişe nokta gösterimini kullanarak erişirsiniz:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Seçme (Tahminler)  
 `select`Yan tümcesi sorgunun sonuçlarını üretir ve döndürülen her öğenin "şeklini" veya türünü belirtir. Örneğin, sonuçlarınızın tam `Customer` nesneler, yalnızca bir üye, bir üye alt kümesi veya bir hesaplama ya da yeni nesne oluşturmaya göre tamamen farklı sonuç türü olacağını belirtebilirsiniz. `select`Yan tümce, kaynak öğenin bir kopyası dışında bir şey üretirse, işleme bir *projeksiyon*olarak adlandırılır. Verileri dönüştürmek için projeksiyonun kullanımı, LINQ sorgu ifadelerinin güçlü bir özelliğidir. Daha fazla bilgi için bkz. [LINQ (C#)](./data-transformations-with-linq.md) ve [Select yan tümcesi](../../../language-reference/keywords/select-clause.md)ile veri dönüştürmeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ sorgu Ifadeleri](../../../linq/index.md)
- [İzlenecek yol: C 'de sorgu yazma #](./walkthrough-writing-queries-linq.md)
- [Sorgu anahtar sözcükleri (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Anonim Türler](../../classes-and-structs/anonymous-types.md)
