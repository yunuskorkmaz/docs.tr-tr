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
ms.openlocfilehash: 013e1960e6c5721e0bd7ce6998848ddce15a4e4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924388"
---
# <a name="basic-linq-query-operations-c"></a>Temel LINQ Sorgu İşlemleri (C#)
Bu konuda sorgu ifadelerine kısa bir giriş [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ve bir sorguda gerçekleştirdiğiniz bazı tipik işlem türleri verilmiştir. Daha ayrıntılı bilgi aşağıdaki konularda yer verilmiştir:  
  
 [LINQ sorgu Ifadeleri](../../linq-query-expressions/index.md)  
  
 [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)  
  
 [İzlenecek yol: Sorguları yazmaC#](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> SQL veya XQuery gibi bir sorgu dili zaten hakkında bilginiz varsa, bu konunun çoğunu atlayabilirsiniz. Sorgu[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ifadelerinde yan tümceler`from` sırası hakkında bilgi edinmek için sonraki bölümde "yan tümce" konusunu okuyun.  
  
## <a name="obtaining-a-data-source"></a>Bir Veri Kaynağı Elde Etme  
 Bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguda, ilk adım veri kaynağını belirtmektir. Çoğu C# programlama dilinde olduğu gibi, kullanılmadan önce bir değişken bildirilmelidir. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Bir sorguda`cust``customers`, yan tümce ilk olarak veri kaynağını () ve *Aralık değişkenini* () tanıtmak için gelir. `from`  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Aralık değişkeni, bir sorgu ifadesinde gerçek yineleme gerçekleşmediğinde `foreach` , döngü içindeki yineleme değişkenine benzer. Sorgu yürütüldüğünde, Aralık değişkeni içindeki `customers`her bir ardışık öğeye başvuru olarak görev yapar. Derleyici türünü `cust`çıkarsanbildiğinden, açıkça belirtmeniz gerekmez. Ek Aralık değişkenleri bir `let` yan tümce tarafından bulunabilir. Daha fazla bilgi için bkz. [Let yan tümcesi](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> Gibi genel olmayan veri kaynakları <xref:System.Collections.ArrayList>için, Aralık değişkeni açıkça yazılmalıdır. Daha fazla bilgi için [nasıl yapılır: LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) ve [from yan tümcesiyle](../../../language-reference/keywords/from-clause.md)bir ArrayList 'i sorgulayın.  
  
## <a name="filtering"></a>Filtreleme  
 Büyük olasılıkla en yaygın sorgu işlemi, bir filtrenin Boole ifadesi biçiminde uygulanmasından kaynaklanıyor olabilir. Filtre sorgunun yalnızca ifadenin true olduğu öğeleri döndürmesine neden olur. Sonuç, `where` yan tümcesi kullanılarak oluşturulur. Etkin filtre, kaynak sırasından hangi öğelerin dışlanacağını belirtir. Aşağıdaki örnekte, yalnızca `customers` Londra 'da bir adresi olan kişiler döndürülür.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Tümce içinde gereken C# `AND` `OR` sayıda filtre ifadesi uygulamak için tanıdık mantıksal ve işleçleri kullanabilirsiniz. `where` Örneğin, yalnızca adı "Devon" olan "Londra `AND` " dan müşterileri döndürmek için aşağıdaki kodu yazarsınız:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Londra veya Paris 'ten müşterileri döndürmek için aşağıdaki kodu yazarsınız:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Sıralama  
 Genellikle döndürülen verileri sıralamak uygundur. `orderby` Yan tümcesi, döndürülen dizideki öğelerin sıralanmakta olan türün varsayılan karşılaştırmasına göre sıralanmasına neden olur. Örneğin, aşağıdaki sorgu sonuçları `Name` özelliği temel alarak sıralamak için genişletilebilir. `Name` Bir dize olduğundan, varsayılan karşılaştırıcı, a 'dan Z 'ye alfabetik bir sıralama gerçekleştirir.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Sonuçları Z 'den A 'ya doğru sırada sıralamak için `orderby…descending` yan tümcesini kullanın.  
  
 Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Gruplandırma  
 Yan `group` tümcesi, sonuçlarınızı belirttiğiniz bir anahtara göre gruplandırmanızı sağlar. Örneğin, `City` Londra veya Paris 'teki tüm müşterilerin ayrı gruplar halinde olması için sonuçların tarafından gruplanmasını belirtebilirsiniz. Bu durumda, `cust.City` anahtardır.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Bir `group` yan tümcesiyle bir sorgu sonlandırdığınızda, sonuçlarınız bir liste listesi alır. Listedeki her öğe, bir `Key` üyeye ve bu anahtar altında gruplanmış bir öğe listesine sahip olan bir nesnedir. Grup dizisi üreten bir sorgu üzerinde yineleme yaparken, iç içe geçmiş `foreach` bir döngü kullanmanız gerekir. Dış döngü her grup üzerinde yinelenir ve iç döngü her bir grubun üyesi üzerinde yinelenir.  
  
 Bir grup işleminin sonuçlarına başvurmanız gerekirse, daha fazla sorgulanabilecek bir tanımlayıcı oluşturmak için `into` anahtar sözcüğünü kullanabilirsiniz. Aşağıdaki sorgu yalnızca ikiden fazla müşteri içeren grupları döndürür:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Daha fazla bilgi için bkz. [Group yan tümcesi](../../../language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Katılma  
 JOIN işlemleri, veri kaynaklarında açıkça Modellenmemiş diziler arasında ilişkiler oluşturur. Örneğin, aynı konuma sahip tüm müşterileri ve dağıtımcıları bulmak için bir JOIN işlemi gerçekleştirebilirsiniz. Yan tümcesinde her zaman veritabanı tabloları yerine nesne koleksiyonları için de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kullanılır. `join`  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 İçindeki yabancı anahtarlar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesne modelinde bir öğe `join` koleksiyonu tutan özellikler olarak temsil edildiği için ,SQL'deyaptığınızkadarsıkkullanmanızgerekmez.[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Örneğin, bir `Customer` nesnesi bir nesne `Order` koleksiyonu içerir. Bir JOIN gerçekleştirmek yerine, siparişe nokta gösterimini kullanarak erişirsiniz:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Seçme (Tahminler)  
 `select` Yan tümcesi sorgunun sonuçlarını üretir ve döndürülen her öğenin "şeklini" veya türünü belirtir. Örneğin, sonuçlarınızın tam `Customer` nesneler, yalnızca bir üye, bir üye alt kümesi veya bir hesaplama ya da yeni nesne oluşturmaya göre tamamen farklı sonuç türü olacağını belirtebilirsiniz. Yan tümce, kaynak öğenin bir kopyası dışında bir şey üretirse, işleme bir projeksiyon olarak adlandırılır. `select` Verileri dönüştürmek için projeksiyonun kullanımı, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinin güçlü bir özelliğidir. Daha fazla bilgi için bkz. [LINQ (C#)](./data-transformations-with-linq.md) ve [Select yan tümcesiyle](../../../language-reference/keywords/select-clause.md)veri dönüştürmeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ sorgu Ifadeleri](../../linq-query-expressions/index.md)
- [İzlenecek yol: Sorguları yazmaC#](./walkthrough-writing-queries-linq.md)
- [Sorgu anahtar sözcükleri (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Anonim Tipler](../../classes-and-structs/anonymous-types.md)
