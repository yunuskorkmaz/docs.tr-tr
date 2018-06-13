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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289405"
---
# <a name="join-clause-c-reference"></a>join tümcesi (C# Başvurusu)
`join` Yan tümcesi nesne modelinde hiçbir doğrudan ilişkisine sahip farklı kaynak sıraları öğelerinden ilişkilendirmek için yararlıdır. Her kaynak öğelerinde eşitlik için karşılaştırılması gereken bazı değeri paylaşmak tek gereksinimdir. Örneğin, belirli bir ürünü tedarikçileri listesini ve alıcıların listesi yemek dağıtıcı olabilir. A `join` yan tümcesi, örneğin, satıcılar listesini oluşturmak için kullanılabilir ve tüm aynı olan alıcılar söz konusu ürünün belirtilen bölge.  
  
 A `join` yan tümcesi iki kaynak sıraları giriş olarak alır. Her dizisi öğelerinde olması veya diğer dizide karşılık gelen bir özellik için karşılaştırılabilir bir özelliği içerir. `join` Yan tümcesi özel kullanarak eşitlik için belirtilen anahtarlara karşılaştırır `equals` anahtar sözcüğü. Tarafından gerçekleştirilen tüm birleştirmeler `join` yan tümcesi olan equijoins. Çıktısını şeklini bir `join` yan tümcesi gerçekleştirme birleştirme belirli türüne bağlıdır. En yaygın üç birleşim türleri şunlardır:  
  
-   iç birleşim  
  
-   Grup birleştirme  
  
-   Sol dış birleşim  
  
## <a name="inner-join"></a>İç birleşim  
 Aşağıdaki örnekte basit bir iç equijoin gösterir. Bu sorgu düz bir dizi üreten "ürün adı / Kategori" çiftleri. Aynı kategori dizesi birden çok öğe görünür. Bir öğeyi varsa `categories` hiçbir eşleşen `products`, kategori sonuçlarında görünmez.  
  
 [!code-csharp[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: İç birleşimler gerçekleştirmek](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).  
  
## <a name="group-join"></a>Group Join  
 A `join` yan tümcesiyle birlikte bir `into` ifadesi, bir grup birleştirme çağrılır.  
  
 [!code-csharp[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]  
  
 Bir grup birleştirme sol kaynak sıradaki öğelerin sağ tarafında kaynak dizideki eşleşen öğelerin bir veya daha fazla ile ilişkilendirir bir hiyerarşik Sonuç dizisi üretir. Bir grup birleştirme eşdeğeri ilişkisel koşullarını sahiptir; nesne dizileri aslında bir dizi var.  
  
 Doğru kaynak serisinden öğe sol kaynağında öğe eşleşecek şekilde bulunursa `join` yan tümcesi, o öğe için boş bir dizi oluşturacak. Sonuç dizisi gruplar halinde düzenlenmiştir bu nedenle, group JOIN hala temelde iç-equijoin olmasıdır.  
  
 Bir grup birleştirme sonuçlarını seçerseniz, öğeleri erişebilirsiniz, ancak bunlar üzerinde eşleşen anahtar tanımlayamıyor. Bu nedenle, önceki örnekte gösterildiği gibi group JOIN sonuçlarını da anahtar adına sahip yeni bir tür seçmek genellikle daha yararlı olacaktır.  
  
 Ayrıca, doğal olarak, bir grup birleştirme sonucu başka bir alt sorgu oluşturucu olarak kullanabilirsiniz:  
  
 [!code-csharp[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: gruplandırılmış gerçekleştirmek birleştirir](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).  
  
## <a name="left-outer-join"></a>Sol dış birleşim  
 Eşleşen bir öğe doğru sırada olsa bile bir sol dış birleştirme, soldaki kaynak dizisindeki tüm öğeler, döndürülür. Bir sol dış birleşim gerçekleştirmek için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], kullanın `DefaultIfEmpty` sol taraftaki öğenin herhangi bir eşleşme varsa üretmek için bir varsayılan sağ taraftaki öğesi belirtmek için bir grup birleştirme ile birlikte yöntemi. Kullanabileceğiniz `null` herhangi bir referans için varsayılan değer olarak türü veya bir kullanıcı tarafından tanımlanan varsayılan türünü belirtebilirsiniz. Aşağıdaki örnekte, bir kullanıcı tarafından tanımlanan varsayılan türü gösterilir:  
  
 [!code-csharp[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: gerçekleştirmek Left Outer JOIN](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).  
  
## <a name="the-equals-operator"></a>Eşittir işleci  
 A `join` yan tümcesi equijoin gerçekleştirir. Diğer bir deyişle, iki anahtar eşitlik yalnızca temel eşleşmeleri ile kullanabilirsiniz. Karşılaştırmaları "büyüktür" veya "eşit değil" gibi diğer türleri desteklenmez. Tüm birleştirmeler equijoins, olduğunu netleştirmek için `join` yan tümcesi kullanan `equals` anahtar sözcüğü yerine `==` işleci. `equals` Anahtar sözcüğü yalnızca kullanılabilir bir `join` yan tümcesi ve farklı olarak `==` önemli bir şekilde işleci. İle `equals`, dış kaynak sırası sol anahtarı kullanır ve iç kaynağı doğru anahtar kullanır. Yalnızca sol tarafındaki kapsamdaki dış kaynağıdır `equals` ve iç kaynak yalnızca sağ tarafında kapsamdaki sırasıdır.  
  
## <a name="non-equijoins"></a>Equijoins olmayan  
 Birleştirmeler ve diğer özel birleştirme işlemleri çapraz olmayan-equijoins, birden çok kullanarak gerçekleştirebileceğiniz `from` yeni dizileri bağımsız olarak bir sorgu tanıtmak için yan tümceleri. Daha fazla bilgi için bkz: [nasıl yapılır: özel birleştirme işlemleri gerçekleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="joins-on-object-collections-vs-relational-tables"></a>Nesne koleksiyonları ilişkisel tablolar ve birleşimler  
 İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadesi, birleştirme işlemleri nesne koleksiyonları üzerinde gerçekleştirilir. Nesne koleksiyonları "iki ilişkisel tablolar tam olarak aynı şekilde katılamaz". İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], açık `join` yan tümceleri, yalnızca iki kaynak sıraları tarafından herhangi bir ilişki bağlanmayan gereklidir. İle çalışırken [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], yabancı anahtar tablolar temsil edilen nesne modelinde birincil tablo özellikleri olarak. Örneğin, Northwind veritabanında müşteri tablosu ile Siparişler tablosundaki yabancı anahtar ilişkisi vardır. Nesne modeli tabloları eşlediğinizde, müşteri sınıfı bu müşteriyle ilişkili siparişleri koleksiyonunu içerir bir sipariş özelliğine sahiptir. Aslında, birleştirme zaten sizin için yapılmıştır.  
  
 Bağlamında ilişkili tablolar arasında sorgulama hakkında daha fazla bilgi için [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], bkz: [nasıl yapılır: eşleme veritabanı ilişkileri](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
## <a name="composite-keys"></a>Bileşik anahtarlar  
 Bileşik bir anahtar kullanarak birden çok değer eşitlik için test edebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bileşik anahtarlar kullanarak tarafından katılma](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md). Bileşik anahtarlar da kullanılabilir bir `group` yan tümcesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir iç birleştirme, bir grup birleştirme ve bir sol dış birleşim aynı veri kaynaklarında sonuçlarını aynı eşleşen anahtarlar kullanılarak karşılaştırır. Bazı ek kod konsol görüntü sonuçlarında açıklığa kavuşturmak amacıyla bu örnekleri eklenir.  
  
 [!code-csharp[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 A `join` tarafından izlenmeyen yan tümcesi `into` erişimcisine bir <xref:System.Linq.Enumerable.Join%2A> yöntem çağrısı. A `join` ile devam eden yan tümcesi `into` için çevrilmiş bir <xref:System.Linq.Enumerable.GroupJoin%2A> yöntem çağrısı.  
  
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
