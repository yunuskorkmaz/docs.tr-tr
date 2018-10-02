---
title: from tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: c8c124f44df292b8323560cce541cca2765e2790
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863240"
---
# <a name="from-clause-c-reference"></a>from tümcesi (C# Başvurusu)

Sorgu ifadesi ile başlamalıdır bir `from` yan tümcesi. Ayrıca, bir sorgu ifadesi de şununla alt sorgularda içerebilir bir `from` yan tümcesi. `from` Yan tümcesi şunları belirtir:

- Veri kaynağı üzerinde sorgu veya alt sorgu çalıştırılır.

- Yerel bir *aralık değişkeni* , kaynak dizideki her öğe temsil eder.

Veri kaynağı ve aralık değişkeni kesin türlü yapılır. Başvurulan veri kaynağı `from` yan tümcesi, bir tür olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, veya türetilmiş bir tür gibi <xref:System.Linq.IQueryable%601>.

Aşağıdaki örnekte, `numbers` veri kaynağıdır ve `num` aralık değişkeni. Her iki değişken olsa bile kesin olarak belirlenmiştir, Not [var](var.md) anahtar sözcüğü kullanılır.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Aralık değişkeni

Veri kaynağı uygular, derleyici Aralık değişkeninin türünü çıkarsar <xref:System.Collections.Generic.IEnumerable%601>. Örneğin, kaynak türü varsa `IEnumerable<Customer>`, aralık değişkeni olması sorguluyorsanız `Customer`. Açıkça türüdür ne zaman belirtmelisiniz. yalnızca bir kez kaynağı olan genel olmayan `IEnumerable` gibi yazın <xref:System.Collections.ArrayList>. Daha fazla bilgi için [nasıl yapılır: LINQ ile ArrayList sorgulama](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

Önceki örnekte `num` türünde olmasını çıkarılan `int`. Aralık değişkeninin türü kesin olarak belirtilmiş olduğundan üzerinde yöntemleri çağırmak ya da diğer işlemleri kullanın. Örneğin, yazmak yerine `select num`, şunu yazabilirsiniz `select num.ToString()` dize yerine tamsayı bir dizisini döndürmek sorgu ifadesi neden olacak. Veya şunu yazabilirsiniz `select n + 10` 14 dizisini döndürmek için ifadeyi neden 11, 13, 12, 10. Daha fazla bilgi için [select yan tümcesi](select-clause.md).

Bir yineleme değişkeni aralık değişkeni benzer bir [foreach](foreach-in.md) çok önemli bir fark dışında deyimi: bir aralık değişkenine asla gerçekten kaynaktan gelen verileri depolar. Bu sorgu yürütüldüğünde yalnızca sağlayan ne açıklamak sorgu söz dizimi kolaylık meydana gelir. Daha fazla bilgi için [(C#) LINQ sorgularına giriş](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Bileşik yan tümcelerinden

Bazı durumlarda, kaynak dizideki her öğe kendisi ya da bir dizi veya bir dizisini içerir. Örneğin, veri kaynağınızın olabilir bir `IEnumerable<Student>` burada dizideki her Öğrenci nesne içeren test puanlarını listesi. Her iç listesine erişmek için `Student` öğesi bileşik kullanabilirsiniz `from` yan tümceleri. Kullanarak içe gibi tekniktir [foreach](foreach-in.md) deyimleri. Ekleyebileceğiniz [burada](partial-method.md) veya [orderby](orderby-clause.md) ya da yan tümceleri `from` sonuçları filtrelemek için yan tümcesi. Aşağıdaki örnek, bir dizi gösterir `Student` her biri içeren bir iç nesneler `List` tamsayılar temsil eden test puanlarını. İç listesine erişmek için bileşik kullanın `from` yan tümcesi. İkisi arasındaki yan tümce ekleyebilirsiniz `from` yan tümceleri gerekirse.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Birleştirmeler gerçekleştirme için birden çok yan tümceleri'den kullanma

Bileşik `from` yan tümcesi, tek bir veri kaynağındaki iç koleksiyonlara erişmek için kullanılır. Ancak, bir sorgu birden çok de içerebilir `from` yan tümceleri bağımsız veri kaynaklarından ek sorgular oluşturun. Belirli türlerini kullanarak mümkün olmayan birleştirme işlemleri gerçekleştirmek Bu teknik sayesinde [JOIN yan tümcesi](join-clause.md).

Aşağıdaki örnekte gösterildiği nasıl iki `from` yan tümceleri, iki veri kaynaklarının tam çapraz birleştirme oluşturmak için kullanılabilir.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Birden çok kullanan birleştirme işlemleri hakkında daha fazla bilgi için `from` yan tümcesi bkz [sol dış birleştirmeler gerçekleştirme](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)  
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)  
