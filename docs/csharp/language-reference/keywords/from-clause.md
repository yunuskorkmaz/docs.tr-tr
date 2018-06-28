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
ms.openlocfilehash: e8bb7782fc60a3af20d5926e609a5edea68fd1a3
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027986"
---
# <a name="from-clause-c-reference"></a>from tümcesi (C# Başvurusu)

Bir sorgu ifadesi ile başlamalıdır bir `from` yan tümcesi. Ayrıca, bir sorgu ifadesi de ile başlayan alt sorgularda içerebilir bir `from` yan tümcesi. `from` Yan tümcesi aşağıdaki belirtir:

- Veri kaynağı üzerinde sorgu veya alt sorgu çalıştırılır.

- Yerel *aralık değişkeni* , kaynak sıradaki her bir öğesinde temsil eder.

Aralık değişkeni ve veri kaynağı kesin türü belirtilmiş. Başvurulan veri kaynağı `from` yan tümcesi, bir tür olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, veya türetilmiş bir tür gibi <xref:System.Linq.IQueryable%601>.

Aşağıdaki örnekte, `numbers` veri kaynağı ve `num` aralık değişkeni. Her iki değişken kesinlikle bile ile yazılan Not [var](var.md) anahtar sözcüğü kullanılır.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Aralık değişkeni

Implements veri kaynağı zaman derleyici aralık değişkeni türü oluşturur <xref:System.Collections.Generic.IEnumerable%601>. Örneğin, bir kaynak türü `IEnumerable<Customer>`, aralık değişkeni olarak algılanır sonra `Customer`. Açıkça türüdür ne zaman belirtmelisiniz yalnızca bir kez kaynağıdır genel olmayan `IEnumerable` gibi yazın <xref:System.Collections.ArrayList>. Daha fazla bilgi için bkz: [nasıl yapılır: LINQ ile ArrayList sorgulama](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

Önceki örnekte `num` türünde olması olayla `int`. Aralık değişkeni kesin türü belirtilmiş olduğundan üzerinde yöntemlerini çağıran veya diğer işlemlerini kullanın. Örneğin, yazma yerine `select num`, yazma `select num.ToString()` bir dizi dize tamsayılar yerine döndürmek sorgu ifadesi neden olacak. Veya, yazabilirsiniz `select n + 10` dizisi 14, döndürülecek ifade neden 11, 13, 12, 10. Daha fazla bilgi için bkz: [select yan tümcesi](select-clause.md).

Bir yineleme değişkeni aralık değişkeni benzer bir [foreach](foreach-in.md) çok önemli bir fark dışında deyimi: aralık değişkeni aslında hiç veri kaynağından depolar. Bu sorgunun yürütüldüğü zaman yalnızca ne açıklamak sorgu sağlayan bir söz dizim kolaylık meydana gelir. Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Yan tümceleri bileşik

Bazı durumlarda, kaynak sıradaki her bir öğesinde kendisi ya da bir dizi veya olabilir bir dizisini içerir. Örneğin, veri kaynağınız olabilir bir `IEnumerable<Student>` burada her Öğrenci nesne dizisinin test puanları listesini içerir. Her iç listesine erişmek için `Student` öğesi, kullanabileceğiniz bileşik `from` yan tümceleri. Kullanarak iç içe geçmiş gibi tekniktir [foreach](foreach-in.md) deyimleri. Ekleyebileceğiniz [nerede](partial-method.md) veya [orderby](orderby-clause.md) ya da yan tümceleri `from` sonuçlara filtre uygulamak için yan tümcesi. Aşağıdaki örnek, bir dizi gösterir `Student` nesneleri, her biri içeren bir iç `List` tamsayılar puanları test temsil eden. İç listesine erişmek için bileşik kullanmak `from` yan tümcesi. İkisi arasındaki yan tümceleri ekleyebilirsiniz `from` yan tümceleri gerekiyorsa.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Birleştirmeler gerçekleştirme için birden çok from yan tümcesi kullanma

Bileşik `from` yan tümcesi iç koleksiyonlarda tek bir veri kaynağına erişmek için kullanılır. Ancak, bir sorgu birden çok de içerebilir `from` bağımsız veri kaynaklarından ek sorgular oluşturmak yan tümceleri. Bu yöntem, belirli türde bir kullanarak mümkün olmayan birleştirme işlemleri gerçekleştirmenizi sağlar [JOIN yan tümcesi](join-clause.md).

Aşağıdaki örnekte gösterildiği nasıl iki `from` yan tümceleri, iki veri kaynaklarının tam çapraz birleştirme oluşturmak için kullanılabilir.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Birden çok kullanmak birleştirme işlemleri hakkında daha fazla bilgi için `from` yan tümceleri, bkz: [sol dış birleştirmeler gerçekleştirme](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Ayrıca bkz.

[Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)  
[Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)  