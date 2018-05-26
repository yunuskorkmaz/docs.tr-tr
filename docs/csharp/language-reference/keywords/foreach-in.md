---
title: foreach, in (C# Başvurusu)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: b6b7dc0a4d3970ddfbbb6635ccebbbd5b75671e4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
---
# <a name="foreach-in-c-reference"></a>foreach, in (C# Başvurusu)

`foreach` Deyimini uygulayan türünün bir örneği bir deyim veya her öğe için deyimleri bloğu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi. `foreach` Deyimi bu türlerde sınırlı değildir ve aşağıdaki koşulları karşılayan herhangi bir türde bir örneğine uygulanabilir:

- Parametresiz ortak olan `GetEnumerator` yöntemi, dönüş türü olan sınıf, yapı veya arabirim türü
- dönüş türü `GetEnumerator` yöntemi ortak olan `Current` özelliği ve parametresiz ortak `MoveNext` yöntemi, dönüş türü olan <xref:System.Boolean>.

Bir oranda noktası içinde `foreach` deyimi bloğu, bölün dışında döngü kullanarak [sonu](break.md) anahtar sözcüğü ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) anahtar sözcüğü. Ayrıca çıkabilirsiniz bir `foreach` tarafından döngü [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.

## <a name="examples"></a>Örnekler

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek kullanımını gösterir `foreach` örneği deyimiyle <xref:System.Collections.Generic.List%601> uygulayan tür <xref:System.Collections.Generic.IEnumerable%601> arabirimi:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Sonraki örnek kullanır `foreach` örneği deyimiyle <xref:System.Span%601?displayProperty=nameWithType> arabirimlerden uygulamaz türü:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

[Foreach deyimi (C# dil belirtimi)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[Dizilerle foreach kullanma](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[Yineleme Deyimleri](iteration-statements.md)  
[C# Anahtar Sözcükleri](index.md)  
[C# başvurusu](../index.md)  
[C# Programlama Kılavuzu](../../programming-guide/index.md)  