---
title: join tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: a868c52cf753b1e4285586ec41c1993f519299d7
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243728"
---
# <a name="join-clause-c-reference"></a>join tümcesi (C# Başvurusu)
`join` Yan tümcesi, nesne modelinde hiçbir doğrudan ilişkisi olan farklı kaynak dizilerinden öğelerini ilişkilendirmek için kullanışlıdır. Her kaynak öğeleri eşitlik için karşılaştırılması gereken bazı değeri paylaşmak tek gereksinim olmasıdır. Örneğin, bir yiyecek dağıtımcısı, belirli bir ürünü tedarikçileri listesini ve alıcıların listesi sahip olabilir. A `join` yan tümcesi, örneğin, üreticiler listesini oluşturmak için kullanılabilir ve tüm aynı olan alıcılar bu ürünün belirtilen bölge.  
  
 A `join` yan tümcesi, iki kaynak dizileri girdi alır. Her bir dizideki öğelerin olması veya diğer dizisindeki karşılık gelen bir özellik için karşılaştırılabilir bir özelliği içerir. `join` Yan tümcesi, özel kullanarak eşitlik için belirtilen anahtarları karşılaştırır `equals` anahtar sözcüğü. Tarafından gerçekleştirilen tüm birleştirmeler `join` yan tümcesi olan equijoins. Çıkışı şeklini bir `join` yan tümcesi yapmakta olduğunuz birleştirme belirli türüne göre değişir. En yaygın üç birleşim türleri şunlardır:  
  
-   İç birleştirme  
  
-   Grup birleştirme  
  
-   Sol dış birleştirme  
  
## <a name="inner-join"></a>İç birleştirme  
 Aşağıdaki örnek, basit bir iç equijoin gösterir. Bu sorgu düz dizisi üretir "ürün adı / kategorisi" çiftleri. Aynı kategori dize birden çok öğe görünür. Bir öğeyi, `categories` eşleşen yok `products`, bu kategoriye sonuçlarında görünmez.  
  
 [!code-csharp[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]  
  
 Daha fazla bilgi için [nasıl yapılır: iç birleştirmeler gerçekleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).  
  
## <a name="group-join"></a>Group Join  
 A `join` yan tümcesiyle birlikte bir `into` ifadesi, bir grup birleştirme çağrılır.  
  
 [!code-csharp[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]  
  
 Grup birleştirme sağ tarafındaki kaynak dizideki eşleşen öğelerin bir veya daha fazla sol kaynak dizisinin öğelerini ilişkilendirir bir hiyerarşik bir sonuç dizisi üretir. Grup birleştirme eşdeğeri ilişkisel koşullarını vardır. Bu temelde bir nesne dizisidir.  
  
 Öğenin sol kaynakta, eşleştirilecek öğe için doğru kaynak sırasından bulunursa `join` yan tümcesi, o öğe için boş bir dizi üretir. Sonuç dizisi gruplar halinde düzenlenir. Bu nedenle, group JOIN hala temelde iç-equijoin olmasıdır.  
  
 Grup birleştirme sonuçlarını seçmeniz yeterlidir, öğelere erişebilirsiniz, ancak bunlar üzerinde eşleşen anahtar tanımlayamaz. Bu nedenle, önceki örnekte gösterildiği gibi anahtar adı olan yeni bir türe group JOIN sonuçlarını seçin genel olarak daha yararlı olur.  
  
 Ayrıca, bir grup birleştirme sonucu başka bir alt sorgu oluşturucu olarak kullanabilirsiniz:  
  
 [!code-csharp[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]  
  
 Daha fazla bilgi için [nasıl yapılır: gruplandırılmış birleştirmeler gerçekleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).  
  
## <a name="left-outer-join"></a>Sol dış birleştirme  
 Eşleşen bir öğe doğru sırada olsa bile bir sol dış birleştirme, soldaki kaynak dizisindeki tüm öğeleri, döndürülür. Bir sol dış birleştirme gerçekleştirmek için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], kullanın `DefaultIfEmpty` sol taraftaki öğesi herhangi bir eşleşme varsa üretmek için bir varsayılan sağ taraftaki öğesi belirtmek için bir grup birleştirme birlikte yöntemi. Kullanabileceğiniz `null` olarak herhangi bir referans için varsayılan değer türü veya bir kullanıcı tanımlı tür belirtebilirsiniz. Aşağıdaki örnekte, bir kullanıcı tarafından tanımlanan varsayılan türü gösterilmiştir:  
  
 [!code-csharp[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]  
  
 Daha fazla bilgi için [nasıl yapılır: gerçekleştirmek Left Outer JOIN](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).  
  
## <a name="the-equals-operator"></a>Eşittir işleci  
 A `join` yan tümcesi equijoin gerçekleştirir. Diğer bir deyişle, iki anahtar eşitlik yalnızca temel eşleşmeleri ile kullanabilirsiniz. Karşılaştırma "büyük" veya "eşit değildir" gibi diğer türleri desteklenmez. Tüm birleştirmeler equijoins, olduğunu netleştirmek için `join` yan tümcesi kullanan `equals` anahtar sözcüğü yerine `==` işleci. `equals` Anahtar sözcüğü yalnızca kullanılabilir bir `join` yan tümcesi ve farklıdır `==` önemli bir şekilde işleci. İle `equals`sol ok tuşu dış kaynak dizisini tüketir ve sağ ok tuşu iç kaynak kullanır. Yalnızca sol tarafındaki kapsamda dış kaynağıdır `equals` ve iç kaynak yalnızca işlecin sağ tarafındaki kapsamda sırasıdır.  
  
## <a name="non-equijoins"></a>Equijoins olmayan  
 Çapraz birleştirme ve diğer özel birleştirme işlemleri olmayan-equijoins, birden çok kullanarak gerçekleştirebileceğiniz `from` yeni dizileri bağımsız olarak bir sorguya tanıtmak amacıyla yan tümceler. Daha fazla bilgi için [nasıl yapılır: özel birleştirme işlemleri gerçekleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="joins-on-object-collections-vs-relational-tables"></a>Nesnesi koleksiyonlar ilişkisel tabloları ve birleşimler  
 İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadesinde, birleştirme işlemleri, nesne koleksiyonları üzerinde gerçekleştirilir. Nesne koleksiyonları "iki ilişkisel tabloları tam olarak aynı şekilde katılamaz". İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], açık `join` yan tümceleri, yalnızca iki kaynak dizileri tarafından herhangi bir ilişki bağlanmayan gereklidir. İle çalışırken [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], yabancı anahtar tabloları nesne modelinde birincil tablo özellikleri olarak temsil edilir. Örneğin, Northwind veritabanında yabancı anahtar ilişkisi Siparişler tablosu ile müşteri tablosu vardır. Tablolar için nesne modeli eşlediğinizde, müşteri sınıfı bu müşteriyle ilgili Siparişler topluluğu içeren bir sipariş özelliğine sahiptir. Aslında, birleştirme zaten sizin için yapılmıştır.  
  
 Bağlamında ilgili tablolar üzerinden sorgulama hakkında daha fazla bilgi için [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], bkz: [nasıl yapılır: veritabanı ilişkilerini eşleme](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
## <a name="composite-keys"></a>Bileşik anahtarlar  
 Bir bileşik anahtarı kullanılarak birden çok değer eşitliği test edebilirsiniz. Daha fazla bilgi için [nasıl yapılır: bileşik anahtarlar kullanarak tarafından katılın](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md). Bileşik anahtarlar da kullanılabilir bir `group` yan tümcesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aynı eşleşen anahtarlar kullanılarak bir iç birleştirme, bir grup katma ve aynı veri kaynaklarında bir sol dış birleştirme sonuçlarının karşılaştırır. Bazı ek bir kod sonuçları konsol açıklamak için bu örnekleri eklenir.  
  
 [!code-csharp[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 A `join` tarafından izlenmiyor yan tümcesi `into` erişimcisine bir <xref:System.Linq.Enumerable.Join%2A> yöntem çağrısı. A `join` takip yan tümcesi `into` çevrildiğinde bir <xref:System.Linq.Enumerable.GroupJoin%2A> yöntem çağrısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu anahtar sözcükleri (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Birleştirme İşlemleri](../../programming-guide/concepts/linq/join-operations.md)  
 [group yan tümcesi](../../../csharp/language-reference/keywords/group-clause.md)  
 [Nasıl yapılır: sol dış birleştirmeler gerçekleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Nasıl yapılır: iç birleştirmeler gerçekleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Nasıl yapılır: gruplandırılmış birleştirmeler gerçekleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Nasıl yapılır: Join tümcesinin sonuçlarını sıralama](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Nasıl yapılır: bileşik anahtarlar kullanarak birleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Nasıl yapılır: örnek veritabanları yükleme](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
