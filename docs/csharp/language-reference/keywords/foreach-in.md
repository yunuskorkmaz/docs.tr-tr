---
title: C# foreach deyimi
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: dbe4f4e95c2b99f1be47885e39d51db81ba3a97d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173711"
---
# <a name="foreach-in-c-reference"></a>foreach, in (C# referans)

Deyim, `foreach` her öğe için bir deyim <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> ifade bloğu uygular türü veya arabirimi uygulayan bir örnek teveks. Bildirim `foreach` bu türlerle sınırlı değildir ve aşağıdaki koşulları yerine getiren herhangi bir türe uygulanabilir:

- dönüş türü sınıf, `GetEnumerator` yapı veya arayüz türü olan ortak parametresiz yönteme sahiptir,
- yöntemin `GetEnumerator` dönüş türü kamu `Current` malı ve geri dönüş `MoveNext` türü olan <xref:System.Boolean>kamu parametresiz yöntemi vardır.

C# 7.3 ile başlayarak, numaralandırıcının `Current` özelliği bir referans dönüş `T` [değeri](ref.md#reference-return-values) döndürürse (toplama`ref T` öğesinin türü nerede), yineleme değişkenini veya `ref` `ref readonly` değiştiriciile birlikte bildirebilirsiniz.

C# 8.0 ile `await` başlayarak, koleksiyon `foreach` türü arabirimi uyguladığında <xref:System.Collections.Generic.IAsyncEnumerable%601> işleç deyimine uygulanabilir. Döngünün her yinelemesi, bir sonraki öğe eş senkronize olarak alınırken askıya alınabilir. Varsayılan olarak, akış öğeleri yakalanan bağlamında işlenir. Bağlamın ele geçirilmesini devre dışı kılmış <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> olmak istiyorsanız, uzantı yöntemini kullanın. Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi [için, Görev tabanlı eşzamanlı deseni tüketme makalesine](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)bakın.

İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilir veya continue deyimini kullanarak döngüdeki bir sonraki yinelemeye adım atabilirsiniz. [continue](continue.md) `foreach` Ayrıca `foreach` [goto,](goto.md) [return](return.md)veya [atmak](throw.md) ifadeleri tarafından bir döngü çıkabilirsiniz.

İfadesi `foreach` `null`uygulanırsa, <xref:System.NullReferenceException> a atılır. `foreach` İfadenin kaynak koleksiyonu boşsa, `foreach` döngügövdesi yürütülmez ve atlanır.

## <a name="examples"></a>Örnekler

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, ifadenin `foreach` <xref:System.Collections.Generic.IEnumerable%601> arabirimi uygulayan <xref:System.Collections.Generic.List%601> türe ait bir örneği yle kullanımını gösterir:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Sonraki örnek, `foreach` herhangi bir arabirim <xref:System.Span%601?displayProperty=nameWithType> uygulamaz türü, bir örnek ile deyimi kullanır:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Aşağıdaki örnek, `ref` stackalloc dizisindeher öğenin değerini ayarlamak için bir yineleme değişkeni kullanır. Sürüm, `ref readonly` tüm değerleri yazdırmak için koleksiyonu yineler. Bildirimde `readonly` örtülü yerel değişken bildirimi kullanır. Örtük değişken bildirimleri, `ref` açıkça `ref readonly` yazılan değişken bildirimleri gibi, ya da bildirimleri ile kullanılabilir.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

Aşağıdaki örnek, `await foreach` her öğeyi eşit olarak oluşturan bir koleksiyonu yinelemek için kullanır:

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [foreach deyimi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Foreach'i dizilerle kullanma](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [ifade için](for.md)
