---
title: C# foreach ifadesi
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401894"
---
# <a name="foreach-in-c-reference"></a>foreach, in (C# Başvurusu)

`foreach`Deyimi, veya arabirimini uygulayan tür örneğindeki her öğe için bir deyimi veya bir deyim bloğunu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> . `foreach`Deyimleri bu türlerle sınırlı değildir ve aşağıdaki koşullara uyan herhangi bir türün örneğine uygulanabilir:

- , `GetEnumerator` dönüş türü Class, struct veya Interface türünde olan public parametresiz metoda sahiptir
- metodun dönüş türü, `GetEnumerator` ortak `Current` özelliğine ve dönüş türü olan public parametresiz metoda sahiptir `MoveNext` <xref:System.Boolean> .

Çoğu kullanımda, `foreach` `IEnumerable<T>` her öğe türünde olan bir ifadeyi yineler `T` . Ancak öğeler, özelliğin türünden örtük veya açık dönüştürmeye sahip herhangi bir tür olabilir `Current` . `Current`Özelliği döndürürse `SomeType` , öğelerin türü şu olabilir:

- Temel sınıflarından herhangi biri `SomeType` .
- Tarafından uygulanan arabirimlerden herhangi biri `SomeType` .

Ayrıca, `SomeType` bir veya ise, `class` `interface` `sealed` öğelerin türü şunları içerebilir:

- Öğesinden türetilmiş herhangi bir tür `SomeType` .
- Herhangi bir rastgele arabirim. Herhangi bir arabirim, veya uygulamadan türetilmiş bir sınıf tarafından uygulanabileceğinden, herhangi bir arabirime izin verilir `SomeType` .

Önceki kurallarla eşleşen herhangi bir türü kullanarak yineleme değişkenini bildirebilirsiniz. `SomeType`Yineleme değişkeninin türüne dönüştürme, açık bir dönüştürme gerektiriyorsa, bu işlem <xref:System.InvalidCastException> dönüştürme başarısız olduğunda bir oluşturabilir.

C# 7,3 ile başlayarak, Numaralandırıcı `Current` özelliği bir [Başvuru dönüş değeri](ref.md#reference-return-values) döndürürse ( `ref T` burada `T` koleksiyon öğesinin türüdür), yineleme değişkenini `ref` veya `ref readonly` değiştiriciyle bildirebilirsiniz.

C# 8,0 ' den başlayarak, `await` `foreach` koleksiyon türü arabirimini uygularsa işleç ifadeye uygulanabilir <xref:System.Collections.Generic.IAsyncEnumerable%601> . Next öğesi zaman uyumsuz olarak alındığında döngünün her yinelemesi askıya alınabilir. Akış öğeleri varsayılan olarak yakalanan bağlamda işlenir. Bağlam yakalamayı devre dışı bırakmak istiyorsanız, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> genişletme yöntemini kullanın. Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz model](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanma başlıklı makaleye bakın.

Deyimdeki herhangi bir noktada `foreach` , [Break](break.md) ifadesini kullanarak ya da [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adımla döngüyü kesebilirsiniz. Ayrıca `foreach` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.

`foreach`İfade öğesine uygulanırsa `null` , bir oluşturulur <xref:System.NullReferenceException> . Deyimin kaynak koleksiyonu `foreach` boşsa, `foreach` Döngünün gövdesi yürütülmez ve atlanır.

## <a name="examples"></a>Örnekler

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, `foreach` arabirimini uygulayan türünün bir örneği ile deyimin kullanımını gösterir <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.IEnumerable%601> :

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

Sonraki örnek, `foreach` <xref:System.Span%601?displayProperty=nameWithType> hiçbir arabirim uygulamayan türü bir örneği ile ifadesini kullanır:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

Aşağıdaki örnek, bir `ref` stackalloc dizisindeki her bir öğenin değerini ayarlamak için bir yineleme değişkeni kullanır. `ref readonly`Sürüm, tüm değerleri yazdırmak için koleksiyonu yineler. `readonly`Bildirim örtük bir yerel değişken bildirimi kullanır. Örtük değişken bildirimleri, ya da `ref` `ref readonly` bildirimleriyle birlikte kullanılabilir ve açıkça değişken bildirimleri olarak türlenebilir.

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

Aşağıdaki örnek, `await foreach` her öğeyi zaman uyumsuz olarak üreten bir koleksiyonu yinelemek için kullanır:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [foreach ifadesi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Dizilerle foreach kullanma](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for deyimi](for.md)
