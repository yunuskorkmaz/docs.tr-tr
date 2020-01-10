---
title: from yan tümcesi C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 388b9c0245b112d619fc173f6019b3f7dbf59940
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715287"
---
# <a name="from-clause-c-reference"></a>from tümcesi (C# Başvurusu)

Sorgu ifadesinin bir `from` yan tümcesiyle başlaması gerekir. Ayrıca, bir sorgu ifadesi Ayrıca bir `from` yan tümcesiyle başlayan alt sorgular içerebilir. `from` yan tümcesi şunları belirtir:

- Sorgu veya alt sorgunun çalıştırılacağı veri kaynağı.

- Kaynak dizideki her öğeyi temsil eden yerel bir *Aralık değişkeni* .

Hem Aralık değişkeni hem de veri kaynağı kesin olarak türdedir. `from` yan tümcesinde başvurulan veri kaynağı bir tür <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>veya <xref:System.Linq.IQueryable%601>gibi türetilmiş bir tür olmalıdır.

Aşağıdaki örnekte, `numbers` veri kaynağıdır ve `num` Aralık değişkenidir. Aynı [anahtar sözcüğünün kullanıldığı halde, her](var.md) iki değişkenin de kesin olarak yazıldığına göz önünde varın.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Aralık değişkeni

Derleyici, veri kaynağı <xref:System.Collections.Generic.IEnumerable%601>uyguladığı zaman Aralık değişkeninin türünü kullanır. Örneğin, kaynağın bir `IEnumerable<Customer>`türü varsa, Aralık değişkeni `Customer`olarak algılanır. Türü açıkça belirtmeniz gereken tek zaman, kaynak <xref:System.Collections.ArrayList>gibi genel olmayan bir `IEnumerable` türüdür. Daha fazla bilgi için bkz. [LINQ Ile ArrayList 'i sorgulama](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

Önceki örnekte `num` `int`türü olarak algılanır. Aralık değişkeni kesin olarak yazıldığından, üzerinde Yöntemler çağırabilir veya diğer işlemlerde kullanabilirsiniz. Örneğin, `select num`yazmak yerine sorgu ifadesinin tamsayılar yerine dizeler dizisi döndürmesini sağlamak için `select num.ToString()` yazabilirsiniz. Ya da ifadenin 14, 11, 13, 12, 10 sırasını döndürmesini sağlamak için `select num + 10` yazabilirsiniz. Daha fazla bilgi için bkz. [Select yan tümcesi](select-clause.md).

Aralık değişkeni, çok önemli bir fark dışında bir [foreach](foreach-in.md) deyimindeki bir yineleme değişkeni gibidir: bir Aralık değişkeni aslında verileri kaynaktan depolamaz. Sorgu yürütüldüğünde neler olacağını açıklamaya olanak sağlayan, yalnızca sözdizimsel bir kolaylık vardır. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Yan tümcelerden bileşik

Bazı durumlarda, kaynak dizideki her öğe bir sıra ya da bir sıra içerebilir. Örneğin, veri kaynağınız dizideki her öğrenci nesnesinin bir test puanları listesi içerdiği bir `IEnumerable<Student>` olabilir. Her `Student` öğesi içindeki iç listeye erişmek için bileşik `from` yan tümceleri kullanabilirsiniz. Tekniği iç içe geçmiş [foreach](foreach-in.md) deyimlerini kullanma gibidir. Sonuçları filtrelemek için `from` yan tümcesine [WHERE](partial-method.md) veya [OrderBy](orderby-clause.md) yan tümceleri ekleyebilirsiniz. Aşağıdaki örnek, her biri test puanlarını temsil eden tamsayıların iç `List` içeren `Student` nesnelerinin bir dizisini gösterir. İç listeye erişmek için bileşik `from` yan tümcesini kullanın. Gerekirse iki `from` yan tümce arasına yan tümceler ekleyebilirsiniz.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Birleştirme gerçekleştirmek için birden çok from yan tümcesini kullanma

Tek bir veri kaynağındaki iç koleksiyonlara erişmek için bileşik bir `from` yan tümcesi kullanılır. Ancak, bir sorgu bağımsız veri kaynaklarından ek sorgular üreten çoklu `from` yan tümceleri de içerebilir. Bu teknik, [JOIN yan tümcesini](join-clause.md)kullanarak mümkün olmayan belirli tür ekleme işlemlerini gerçekleştirmenize olanak tanır.

Aşağıdaki örnek iki `from` yan tümcelerinin, iki veri kaynağından oluşan bir çapraz birleştirmeyi oluşturmak için nasıl kullanılabileceğini gösterir.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Çoklu `from` yan tümceleri kullanan birleştirme işlemleri hakkında daha fazla bilgi için bkz. [sol dış birleştirmeler gerçekleştirme](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
