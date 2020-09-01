---
description: from yan tümcesi-C# başvurusu
title: from yan tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 474b22f5a9d8f12c8a4365159817f878761b563c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140795"
---
# <a name="from-clause-c-reference"></a>from tümcesi (C# Başvurusu)

Sorgu ifadesinin bir yan tümcesiyle başlaması gerekir `from` . Ek olarak, bir sorgu ifadesi de bir yan tümcesiyle başlayan alt sorgular içerebilir `from` . `from`Yan tümcesi şunları belirtir:

- Sorgu veya alt sorgunun çalıştırılacağı veri kaynağı.

- Kaynak dizideki her öğeyi temsil eden yerel bir *Aralık değişkeni* .

Hem Aralık değişkeni hem de veri kaynağı kesin olarak türdedir. Yan tümcesinde başvurulan veri kaynağı `from` , veya gibi türetilmiş bir türde olmalıdır <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> .

Aşağıdaki örnekte, `numbers` veri kaynağıdır ve `num` Aralık değişkenidir. Aynı [anahtar sözcüğünün kullanıldığı halde, her](var.md) iki değişkenin de kesin olarak yazıldığına göz önünde varın.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Aralık değişkeni

Derleyici, veri kaynağı tarafından çalıştırıldığında Aralık değişkeninin türünü kullanır <xref:System.Collections.Generic.IEnumerable%601> . Örneğin, kaynak türünde bir tür varsa `IEnumerable<Customer>` , Aralık değişkeni olarak algılanır `Customer` . Türü açıkça belirtmeniz gereken tek zaman, kaynak, gibi genel olmayan bir `IEnumerable` tür olduğunda <xref:System.Collections.ArrayList> . Daha fazla bilgi için bkz. [LINQ Ile ArrayList 'i sorgulama](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

Önceki örnekte türü olarak `num` algılanır `int` . Aralık değişkeni kesin olarak yazıldığından, üzerinde Yöntemler çağırabilir veya diğer işlemlerde kullanabilirsiniz. Örneğin yazmak yerine `select num` , `select num.ToString()` sorgu ifadesinin tamsayılar yerine dizeler dizisi döndürmesini sağlamak için yazabilirsiniz. Ya da `select num + 10` ifadenin 14, 11, 13, 12, 10 sırasını döndürmesini sağlamak için yazabilirsiniz. Daha fazla bilgi için bkz. [Select yan tümcesi](select-clause.md).

Aralık değişkeni, çok önemli bir fark dışında bir [foreach](foreach-in.md) deyimindeki bir yineleme değişkeni gibidir: bir Aralık değişkeni aslında verileri kaynaktan depolamaz. Sorgu yürütüldüğünde neler olacağını açıklamaya olanak sağlayan, yalnızca sözdizimsel bir kolaylık vardır. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Yan tümcelerden bileşik

Bazı durumlarda, kaynak dizideki her öğe bir sıra ya da bir sıra içerebilir. Örneğin, veri kaynağınız `IEnumerable<Student>` dizideki her öğrenci nesnesinin bir test puanları listesi içerdiği yerde olabilir. Her öğe içindeki iç listeye erişmek için `Student` bileşik `from` yan tümceleri kullanabilirsiniz. Tekniği iç içe geçmiş [foreach](foreach-in.md) deyimlerini kullanma gibidir. Sonuçları filtrelemek için her iki yan tümce için [WHERE](partial-method.md) veya [OrderBy](orderby-clause.md) yan tümceleri ekleyebilirsiniz `from` . Aşağıdaki örnek `Student` , her biri `List` test puanlarını temsil eden bir tamsayı iç içeren bir nesne dizisi gösterir. İç listeye erişmek için bileşik bir `from` yan tümce kullanın. Gerekirse iki yan tümce arasına yan tümceler ekleyebilirsiniz `from` .

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Birleştirme gerçekleştirmek için birden çok from yan tümcesini kullanma

Bileşik `from` yan tümce, tek bir veri kaynağındaki iç koleksiyonlara erişmek için kullanılır. Ancak, bir sorgu `from` bağımsız veri kaynaklarından ek sorgular üreten birden çok yan tümce de içerebilir. Bu teknik, [JOIN yan tümcesini](join-clause.md)kullanarak mümkün olmayan belirli tür ekleme işlemlerini gerçekleştirmenize olanak tanır.

Aşağıdaki örnek `from` iki veri kaynağının tamamen çapraz bir birleştirmesini oluşturmak için iki yan tümcelerin nasıl kullanılabileceğini gösterir.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Birden çok yan tümce kullanan katılma işlemleri hakkında daha fazla bilgi için `from` bkz. [sol dış birleştirmeler gerçekleştirme](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
