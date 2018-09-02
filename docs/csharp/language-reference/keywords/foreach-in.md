---
title: C# foreach deyimi
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: d84c68eb102d55b31ba20a6b6b5c01b96963924d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405856"
---
# <a name="foreach-in-c-reference"></a>foreach, (C# Başvurusu)

`foreach` Deyimi uygulayan türü örneğinde bir deyimi veya bir her öğe için bir deyimler bloğunu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi. `foreach` Deyimi bu türleri için sınırlı değildir ve aşağıdaki koşulları karşılayan herhangi bir türde bir örneğine uygulanabilir:

- Genel parametresiz `GetEnumerator` yöntemi, dönüş türü olan sınıf, yapı veya arabirim türü
- dönüş türünü `GetEnumerator` yöntemi ortak sahip `Current` özelliği ve parametresiz public `MoveNext` yöntemi, dönüş türü olan <xref:System.Boolean>.

Herhangi bir anda işaret içinde `foreach` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi veya bir sonraki yinelemesine kullanarak adım [devam](continue.md) deyimi. Ayrıca çıkış bir `foreach` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.

## <a name="examples"></a>Örnekler

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, kullanımını gösterir. `foreach` örneği deyimiyle <xref:System.Collections.Generic.List%601> uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> arabirimi:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Sonraki örnekte `foreach` örneği deyimiyle <xref:System.Span%601?displayProperty=nameWithType> arabirimlerden uygulamayan türü:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

C# 7.3, ile başlayarak Numaralandırıcı `Current` özelliği döndürür bir [başvuru dönüş değeri](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` burada `T` koleksiyon öğesi türü), yineleme değişkeni ile bildirebilirsiniz `ref` veya `ref readonly` değiştiricisi. Aşağıdaki örnekte bir `ref` bir stackalloc dizideki her öğenin değerini ayarlamak için yineleme değişkeni. `ref readonly` Sürüm tüm değerleri yazdırmak için koleksiyon yinelenir. `readonly` Bildirimi örtük bir yerel değişken bildirimini kullanır. Örtük değişken bildirimleri ile birlikte kullanılabilir `ref` veya `ref readonly` açıkça mümkün olduğunca bildirimleri, yazdığınız değişken bildirimleri.

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Foreach deyimi (C# dil belirtimi)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)
- [Dizilerle foreach kullanma](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for](for.md)
- [Yineleme Deyimleri](iteration-statements.md)
- [C# Anahtar Sözcükleri](index.md)
- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
