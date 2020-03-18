---
title: join clause - C# Reference
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 8e52e9db241392b67818b7316767dd97bd38432a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713400"
---
# <a name="join-clause-c-reference"></a>join tümcesi (C# Başvurusu)

Yan `join` tümce, nesne modelinde doğrudan ilişkisi olmayan farklı kaynak dizilerinden öğeleri ilişkilendirmede yararlıdır. Tek gereksinim, her kaynaktaki öğelerin eşitlik için karşılaştırılabilen bir değeri paylaşmasıdır. Örneğin, bir gıda dağıtıcısının belirli bir ürünün tedarikçilerinin listesi ve alıcıların listesi olabilir. Bir `join` yan tümce, örneğin, tedarikçiler ve alıcılar ın tüm aynı belirtilen bölgede olan bu ürünün bir listesini oluşturmak için kullanılabilir.

Bir `join` yan tümce giriş olarak iki kaynak dizileri alır. Her dizideki öğeler, diğer sırada karşılık gelen bir özellik ile karşılaştırılabilen bir özellik olmalıdır. Yan `join` tümce, özel `equals` anahtar sözcüğü kullanarak eşitlik için belirtilen anahtarları karşılaştırır. `join` Yan tümek tarafından gerçekleştirilen tüm birleştirmeler denkliktir. Bir `join` yan tümcenin çıktısının şekli, gerçekleştirmekte olduğunuz belirli birleştirme türüne bağlıdır. Aşağıdakiler en yaygın üç birleştirme türüdir:

- İç birleştirme

- Grup birleştirme

- Sol dış birleştirme

## <a name="inner-join"></a>İç birleştirme

Aşağıdaki örnekbasit bir iç equijoin gösterir. Bu sorgu ,"ürün adı / kategorisi" çiftlerinin düz bir sırasını üretir. Aynı kategori dizesi birden çok öğe görünür. Eşleme `products`olmayan `categories` bir öğe varsa, bu kategori sonuçlarda görünmez.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Daha fazla bilgi için [bkz.](../../linq/perform-inner-joins.md)

## <a name="group-join"></a>Grup birleştirme

İfadeiçeren `join` bir `into` yan tümceye grup birleştirme denir.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Grup birleştirme, sol kaynak dizisindeki öğeleri sağ yan kaynak dizisinde bir veya daha fazla eşleşen öğeyle ilişkilendiren hiyerarşik bir sonuç dizisi üretir. Bir grup birleştirme ilişkisel terimler açısından eşdeğeri vardır; aslında nesne dizileri dizisidir.

Sağ kaynak dizisinden hiçbir öğe sol kaynaktaki bir öğeyle `join` eşleşecek şekilde bulunmazsa, yan tümce o öğe için boş bir dizi üretir. Bu nedenle, grup birleştirme hala temelde bir iç-equijoin dışında sonuç sırası gruplar halinde düzenlenir.

Grup birleştirme sonuçlarını seçerseniz, öğelere erişebilirsiniz, ancak eşleştikleri anahtarı tanımlayamazsınız. Bu nedenle, önceki örnekte gösterildiği gibi, grubun birleşme nedenlerini de anahtar adlarIna sahip yeni bir türün katılımını seçmek daha yararlısıdır.

Ayrıca, tabii ki, başka bir alt sorgunun jeneratörolarak bir grup birleştirme sonucunu kullanabilirsiniz:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Daha fazla bilgi için bkz: [Gruplu birleştirmeleri gerçekleştirin.](../../linq/perform-grouped-joins.md)

## <a name="left-outer-join"></a>Sol dış birleştirme

Sol dış birleştirmede, eşleşen öğeler doğru sırada olmasa bile sol kaynak dizisindeki tüm öğeler döndürülür. LINQ'da sol dış birleştirme gerçekleştirmek `DefaultIfEmpty` için, sol tarafta ki öğe eşleşmesi yoksa üretmek için varsayılan sağ taraf öğesini belirtmek için yöntemi grup birleştirmesiyle birlikte kullanın. Herhangi bir `null` başvuru türü için varsayılan değer olarak kullanabilir veya kullanıcı tarafından tanımlanan varsayılan türü belirtebilirsiniz. Aşağıdaki örnekte, kullanıcı tanımlı varsayılan türü gösterilir:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Daha fazla bilgi için [bkz.](../../linq/perform-left-outer-joins.md)

## <a name="the-equals-operator"></a>Eşittir işleci

Bir `join` yan tümce equijoin gerçekleştirir. Başka bir deyişle, eşleşmeleri yalnızca iki anahtarın eşitliğine dayandırabilirsiniz. "Büyük" veya "eşit olmayan" gibi diğer karşılaştırma türleri desteklenmez. Tüm birleştirmelerin eşit olduğunu belirtmek için, `join` yan tümce `equals` `==` operatör yerine anahtar sözcüğü kullanır. `equals` Anahtar kelime yalnızca bir `join` yan tümcede kullanılabilir `==` ve işleçten önemli bir şekilde farklıdır. Ile `equals`, sol anahtar dış kaynak dizisi tüketir ve sağ anahtar iç kaynak tüketir. Dış kaynak yalnızca sol tarafında ki `equals` kapsamdadır ve iç kaynak dizisi yalnızca sağ taraftaki kapsamdadır.

## <a name="non-equijoins"></a>Denk olmayanlar

Bir sorguya bağımsız olarak yeni diziler tanıtmak için birden çok `from` yan tümce yi kullanarak, equijoins, çapraz birleştirme ve diğer özel birleştirme işlemleri gerçekleştirebilirsiniz. Daha fazla bilgi için [bkz.](../../linq/perform-custom-join-operations.md)

## <a name="joins-on-object-collections-vs-relational-tables"></a>Nesne koleksiyonlarıile ilişkisel tablolara katılma

LINQ sorgu ifadesinde, birleştirme işlemleri nesne koleksiyonlarında gerçekleştirilir. Nesne koleksiyonları iki ilişkisel tabloyla aynı şekilde "birleşemez". LINQ'da, `join` açık yan tümceler yalnızca iki kaynak dizisi herhangi bir ilişkiyle bağlı olmadığında gereklidir. Çalışma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], yabancı anahtar tabloları birincil tablonun özellikleri olarak nesne modelinde temsil edilir. Örneğin, Northwind veritabanında, Müşteri tablosunun Siparişler tablosuyla yabancı anahtar ilişkisi vardır. Tabloları nesne modeliyle eşlediğinizde, Müşteri sınıfının bu Müşteriyle ilişkili Siparişler koleksiyonunu içeren bir Siparişler özelliği vardır. Sonuç olarak, birleştirme zaten sizin için yapılmıştır.

İlgili tablolar arasında sorgu lama hakkında daha [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]fazla bilgi için [bkz.](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md)

## <a name="composite-keys"></a>Kompozit tuşlar

Bileşik bir anahtar kullanarak birden çok değerin eşitliğini sınayabilirsiniz. Daha fazla bilgi için [bkz: Bileşik tuşları kullanarak Katıl.](../../linq/join-by-using-composite-keys.md) Bileşik tuşlar bir `group` yan tümcede de kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, aynı eşleşen tuşları kullanarak aynı veri kaynaklarında bir iç birleştirme, bir grup birleştirme ve sol dış birleştirme sonuçlarını karşılaştırır. Konsol ekranındaki sonuçları netleştirmek için bu örneklere bazı ekstra kodlar eklenir.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Açıklamalar

Takip `join` `into` edilmeyen bir yan tümce, <xref:System.Linq.Enumerable.Join%2A> bir yöntem çağrısına çevrilir. İzleyen bir `join` yan `into` tümce bir <xref:System.Linq.Enumerable.GroupJoin%2A> yöntem çağrısına çevrilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Anahtar Kelimeleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
- [Birleştirme İşlemleri](../../programming-guide/concepts/linq/join-operations.md)
- [group yan tümcesi](group-clause.md)
- [Sol dış birleşimler gerçekleştirme](../../linq/perform-left-outer-joins.md)
- [İç birleşimler gerçekleştirme](../../linq/perform-inner-joins.md)
- [Gruplanmış birleşimler gerçekleştirme](../../linq/perform-grouped-joins.md)
- [Join yan tümcesinin sonuçlarını sıralama](../../linq/order-the-results-of-a-join-clause.md)
- [Bileşik anahtarlar kullanarak birleştirme](../../linq/join-by-using-composite-keys.md)
- [Visual Studio için uyumlu veritabanı sistemleri](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
