---
title: C#foreach ifadesi
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 9c1521f39dea72b51801a81b13e8a0203956731c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422806"
---
# <a name="foreach-in-c-reference"></a>foreach, in (C# başvuru)

`foreach` deyimi, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimini uygulayan tür örneğindeki her öğe için bir deyimi veya bir deyim bloğunu yürütür. `foreach` deyimleri bu türlerle sınırlı değildir ve aşağıdaki koşullara uyan herhangi bir türün örneğine uygulanabilir:

- , dönüş türü Class, struct veya Interface türünde olan public parametresiz `GetEnumerator` yöntemine sahiptir
- `GetEnumerator` yönteminin dönüş türü, ortak `Current` özelliğine ve dönüş türü <xref:System.Boolean>olan public parametresiz `MoveNext` metoduna sahiptir.

7,3 ile C# başlayarak, numaralandırıcının `Current` özelliği bir [Başvuru dönüş değeri](ref.md#reference-return-values) döndürürse (`T` koleksiyon öğesinin türü olduğu`ref T`), yineleme değişkenini `ref` veya `ref readonly` değiştiricisiyle bildirebilirsiniz.

`foreach` bildiri bloğunun içindeki herhangi bir noktada, [Break](break.md) ifadesini kullanarak döngünün dışına bölebilir veya [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adım aktarabilirsiniz. Ayrıca, [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir `foreach` döngüsünden çıkabilirsiniz.

`foreach` deyimin `null`uygulanmışsa bir <xref:System.NullReferenceException> oluşturulur. `foreach` deyimin kaynak koleksiyonu boşsa, `foreach` döngüsünün gövdesi yürütülmez ve atlanır.

## <a name="examples"></a>Örnekler

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan <xref:System.Collections.Generic.List%601> türünün bir örneği ile `foreach` deyimin kullanımını gösterir:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Sonraki örnek, hiçbir arabirim uygulamayan <xref:System.Span%601?displayProperty=nameWithType> türünün bir örneği ile `foreach` ifadesini kullanır:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Aşağıdaki örnek, bir stackalloc dizisindeki her bir öğenin değerini ayarlamak için bir `ref` yineleme değişkeni kullanır. `ref readonly` sürümü, tüm değerleri yazdırmak için koleksiyonu yineler. `readonly` bildirimi örtük bir yerel değişken bildirimi kullanır. Örtük değişken bildirimleri `ref` veya `ref readonly` bildirimleriyle birlikte kullanılabilir, böylece açıkça değişken bildirimleri bulunabilir.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [foreach ifadesi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Dizilerle foreach kullanma](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for deyimleri](for.md)
