---
title: JOIN yan tümcesi C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 8e52e9db241392b67818b7316767dd97bd38432a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713400"
---
# <a name="join-clause-c-reference"></a>join tümcesi (C# Başvurusu)

`join` yan tümcesi, nesne modelinde doğrudan ilişki bulunmayan farklı kaynak dizilerinden öğeleri ilişkilendirmek için yararlıdır. Tek gereksinim, her kaynaktaki öğelerin eşitlik için karşılaştırılabileceğiniz bazı değerleri paylaşmasına yöneliktir. Örneğin, bir yiyecek dağıtıcısının belirli bir ürünün tedarikçilerinin bir listesi ve alıcıların listesi olabilir. Bir `join` yan tümcesi, örneğin aynı belirtilen bölgede bulunan ürün sağlayıcılarının ve alıcılarının bir listesini oluşturmak için kullanılabilir.

`join` yan tümcesi giriş olarak iki kaynak dizisi alır. Her dizideki öğelerin, başka bir dizide karşılık gelen bir özellik ile karşılaştırılabileceğiniz bir özellik olması veya bir özelliği içermesi gerekir. `join` yan tümcesi, özel `equals` anahtar sözcüğünü kullanarak, eşitlik için belirtilen anahtarları karşılaştırır. `join` yan tümcesi tarafından gerçekleştirilen tüm birleştirmeler, eşbirleşimlerdir. `join` yan tümcesinin çıktısının şekli, gerçekleştirdiğiniz belirli bir JOIN türüne bağlıdır. En yaygın üç JOIN türü aşağıda verilmiştir:

- İç birleşim

- Gruba ekleme

- Sol dış birleşim

## <a name="inner-join"></a>İç birleşim

Aşağıdaki örnek bir basit iç Eş birleşim gösterir. Bu sorgu, "ürün adı/kategori" çiftleri için düz bir dizi oluşturur. Aynı kategori dizesi birden çok öğe içinde görüntülenir. `categories` bir öğeden eşleşen bir `products`yoksa, bu kategori sonuçlarda görünmez.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Daha fazla bilgi için bkz. [İç birleştirmeler gerçekleştirme](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Gruba ekleme

`into` ifadesiyle bir `join` yan tümcesine grup katılımı denir.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Bir grup birleşimi, sol kaynak dizisindeki öğeleri sağ taraftaki kaynak dizisinde bir veya daha fazla eşleşen öğeyle ilişkilendiren hiyerarşik bir sonuç sırası üretir. Bir grup katılımı ilişkisel terimlerle eşdeğer değildir; Aslında bir nesne dizileri dizisidir.

Doğru kaynak dizisinden bir öğe, sol kaynaktaki bir öğeyle eşleşecek şekilde bulunmazsa, `join` yan tümcesi bu öğe için boş bir dizi oluşturur. Bu nedenle, sonuç sırasının gruplar halinde düzenlenme dışında, gruba katılması hala temel olarak bir iç eşbirleştirmedir.

Yalnızca bir grup JOIN 'in sonuçlarını seçerseniz, öğelere erişebilirsiniz, ancak eşleştikleri anahtarı tanımlamazsınız. Bu nedenle, önceki örnekte gösterildiği gibi, Grup birleştirmenin sonuçlarının anahtar adı da olan yeni bir türe katılması genellikle daha yararlıdır.

Ayrıca, başka bir alt sorgunun Oluşturucusu olarak bir grup birleşimi sonucunu da kullanabilirsiniz:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Daha fazla bilgi için bkz. [gruplanmış birleşimler gerçekleştirme](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Sol dış birleşim

Sol dış birleşimde, hiçbir eşleşen öğe doğru sırada olmasa bile, sol kaynak dizideki tüm öğeler döndürülür. LINQ 'te bir sol dış birleşim gerçekleştirmek için, bir sol taraftaki öğenin eşleşmesi yoksa, oluşturmak üzere varsayılan bir sağ taraftaki öğe belirtmek için bir grup birleştirimiyle birlikte `DefaultIfEmpty` yöntemi kullanın. Herhangi bir başvuru türü için varsayılan değer olarak `null` kullanabilir veya Kullanıcı tanımlı varsayılan bir tür belirtebilirsiniz. Aşağıdaki örnekte, Kullanıcı tanımlı varsayılan bir tür gösterilir:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Daha fazla bilgi için bkz. [sol dış birleştirmeler gerçekleştirme](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>Eşittir işleci

`join` yan tümcesi equijoın gerçekleştirir. Diğer bir deyişle, yalnızca iki anahtarın eşitliğine ait eşleşmeleri temel alabilirsiniz. "Büyüktür" veya "Not Equals" gibi diğer karşılaştırma türleri desteklenmez. Tüm birleşimlerin eşbirleştirmelere açık olması için `join` yan tümcesi `==` işleci yerine `equals` anahtar sözcüğünü kullanır. `equals` anahtar sözcüğü yalnızca bir `join` yan tümcesinde kullanılabilir ve `==` işlecinden çok önemli bir şekilde farklılık gösterir. `equals`, sol anahtar dış kaynak sırasını kullanır ve sağ anahtar, iç kaynağı kullanır. Dış kaynak yalnızca `equals` sol tarafındaki kapsamdadır ve iç kaynak sırası yalnızca sağ taraftaki kapsamdadır.

## <a name="non-equijoins"></a>Eşit olmayan birleşimler

Yeni dizileri bir sorguda bağımsız olarak tanıtmak için birden çok `from` yan tümcesini kullanarak, eşlenmemiş olmayan birleşimler, çapraz birleşimler ve diğer özel birleştirme işlemleri gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [özel JOIN Işlemleri gerçekleştirme](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Nesne koleksiyonlarındaki ve ilişkisel tablolardaki birleşimler

Bir LINQ sorgu ifadesinde, nesne koleksiyonlarında JOIN işlemleri gerçekleştirilir. Nesne koleksiyonları, iki ilişkisel tabloyla tamamen aynı şekilde "birleştirilemez". LINQ içinde açık `join` yan tümceleri yalnızca iki kaynak dizisi herhangi bir ilişkiye bağlı olmadığında gereklidir. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]ile çalışırken, yabancı anahtar tabloları nesne modelinde birincil tablonun özellikleri olarak temsil edilir. Örneğin, Northwind veritabanında, müşteri tablosunun Orders tablosuyla bir yabancı anahtar ilişkisi vardır. Tabloları nesne modeliyle eşlediğinizde, müşteri sınıfının bu müşteriyle ilişkili siparişlerin koleksiyonunu içeren bir Orders özelliği vardır. Aslında, birleşimi sizin için zaten yapıldı.

[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]bağlamında ilgili tablolarda sorgulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: veritabanı Ilişkilerini eşleme](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Bileşik anahtarlar

Bileşik anahtar kullanarak birden çok değerin eşitlik için test edebilirsiniz. Daha fazla bilgi için bkz. [bileşik anahtarlar kullanarak ekleme](../../linq/join-by-using-composite-keys.md). Bileşik anahtarlar Ayrıca bir `group` yan tümcesinde de kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, aynı eşleşen anahtarları kullanarak bir iç birleşim, bir grup JOIN ve bir sol dış birleşim sonuçlarını aynı veri kaynakları üzerinde karşılaştırır. Bu örneklere bazı ek kodlar, konsol görüntülerindeki sonuçları açıklığa kavuşturacak şekilde eklenir.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Açıklamalar

`into` tarafından izlenen bir `join` yan tümcesi <xref:System.Linq.Enumerable.Join%2A> yöntem çağrısına çevrilir. `into` tarafından izlenen bir `join` yan tümcesi <xref:System.Linq.Enumerable.GroupJoin%2A> yöntem çağrısına çevrilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
- [Birleştirme İşlemleri](../../programming-guide/concepts/linq/join-operations.md)
- [group yan tümcesi](group-clause.md)
- [Sol dış birleştirmeler gerçekleştirme](../../linq/perform-left-outer-joins.md)
- [İç birleşimler gerçekleştirme](../../linq/perform-inner-joins.md)
- [Gruplanmış birleşimler gerçekleştirme](../../linq/perform-grouped-joins.md)
- [Join yan tümcesinin sonuçlarını sıralama](../../linq/order-the-results-of-a-join-clause.md)
- [Bileşik anahtarlar kullanarak birleştirme](../../linq/join-by-using-composite-keys.md)
- [Visual Studio için uyumlu veritabanı sistemleri](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
