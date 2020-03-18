---
title: fıkradan - C# Referans
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 388b9c0245b112d619fc173f6019b3f7dbf59940
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715287"
---
# <a name="from-clause-c-reference"></a>from tümcesi (C# Başvurusu)

Sorgu ifadesi bir `from` yan tümceyle başlamalıdır. Ayrıca, bir sorgu ifadesi, bir `from` yan tümceyle başlayan alt sorgular da içerebilir. Yan `from` tümce aşağıdakileri belirtir:

- Sorgunun veya alt sorgunun çalıştırılacak veri kaynağı.

- Kaynak dizideki her öğeyi temsil eden yerel *bir aralık değişkeni.*

Hem aralık değişkeni hem de veri kaynağı güçlü bir şekilde yazılır. `from` Yan tümcede başvurulan veri <xref:System.Collections.IEnumerable>kaynağı, <xref:System.Collections.Generic.IEnumerable%601>bir tür , veya türemiş türde <xref:System.Linq.IQueryable%601>olmalıdır.

Aşağıdaki örnekte, `numbers` veri kaynağı `num` ve aralık değişkenidir. [Var](var.md) anahtar sözcüğü kullanılsa bile her iki değişkenin de güçlü bir şekilde yazılmış olduğunu unutmayın.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Aralık değişkeni

Derleyici, veri kaynağı uyguladığında aralık değişkeninin türünü <xref:System.Collections.Generic.IEnumerable%601>çıkartır. Örneğin, kaynak bir türü `IEnumerable<Customer>`varsa, aralık değişkeni olarak `Customer`kabul edilir. Türü açıkça belirtmeniz gereken tek zaman, kaynağın `IEnumerable` <xref:System.Collections.ArrayList>genel olmayan bir tür olmasıdır. Daha fazla bilgi için [LINQ ile ArrayList nasıl sorgulanır.](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)

Önceki örnekte `num` türü `int`nden olduğu kabul edilir. Aralık değişkeni güçlü bir şekilde yazıldığı için, bu değişkendeki yöntemleri arayabilir veya diğer işlemlerde kullanabilirsiniz. Örneğin, yazmak `select num`yerine, sorgu `select num.ToString()` ifadesinin tamsayılar yerine bir dizi dize döndürmesine neden olacak şekilde yazabilirsiniz. Ya da `select num + 10` ifadenin 14, 11, 13, 12, 10 dizisini döndürmesine neden olacak şekilde yazabilirsiniz. Daha fazla bilgi için [bkz.](select-clause.md)

Aralık değişkeni, çok önemli bir fark dışında [her ifadedeki](foreach-in.md) bir yineleme değişkeni gibidir: bir aralık değişkeni hiçbir zaman kaynağından veri depolar. Bu, sorgu yürütüldüğünde ne olacağını açıklayan bir sözdizim kolaylığıdır. Daha fazla bilgi için [LINQ Sorgularına Giriş (C#) 'ye](../../programming-guide/concepts/linq/introduction-to-linq-queries.md)bakın.

## <a name="compound-from-clauses"></a>Yan tümcelerden bileşik

Bazı durumlarda, kaynak dizideki her öğenin kendisi bir dizi olabilir veya bir dizi içerebilir. Örneğin, veri kaynağınız, `IEnumerable<Student>` dizideki her öğrenci nesnesinin test puanlarının bir listesini içerdiği bir kaynak olabilir. Her `Student` öğeiçindeki iç listeye erişmek için `from` bileşik yan tümceleri kullanabilirsiniz. Teknik, iç içe geçen [her ifadeyi](foreach-in.md) kullanmak gibidir. Sonuçları filtrelemek için yan `from` tümceye [nerede](partial-method.md) veya [sıralı](orderby-clause.md) yan tümceler ekleyebilirsiniz. Aşağıdaki örnekte, her `Student` biri test puanlarını temsil `List` eden bir tamsayı içiçeren bir nesne dizisi gösterilmektedir. İç listeye erişmek için bileşik `from` yan tümcekullanın. Gerekirse iki `from` yan tümce arasına yan tümceler ekleyebilirsiniz.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Birleştirme gerçekleştirmek için Yan Tümcelerden Birden Çok Kullanma

Bileşik `from` yan tümce, tek bir veri kaynağındaki iç koleksiyonlara erişmek için kullanılır. Ancak, bir sorgu, `from` bağımsız veri kaynaklarından ek sorgular oluşturan birden çok yan tümce de içerebilir. Bu teknik, [birleştirme yan tümcesini](join-clause.md)kullanarak mümkün olmayan belirli birleştirme işlemleri türlerini gerçekleştirmenizi sağlar.

Aşağıdaki örnek, iki `from` veri kaynağının tam çapraz birliğini oluşturmak için iki yan tümcenin nasıl kullanılabileceğini gösterir.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Birden çok `from` yan tümce kullanan birleştirme işlemleri hakkında daha fazla bilgi için [bkz.](../../linq/perform-left-outer-joins.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Anahtar Kelimeleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
