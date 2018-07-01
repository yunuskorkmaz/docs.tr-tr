---
title: foreach, in (C# Başvurusu)
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: d3ce1122c54c14b1baf35641f28d062a2855d335
ms.sourcegitcommit: 736ec4d3e2c74895b47a0d36126657b95da383c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2018
ms.locfileid: "37140274"
---
# <a name="foreach-in-c-reference"></a>foreach, in (C# Başvurusu)

`foreach` Deyimini uygulayan türünün bir örneği bir deyim veya her öğe için deyimleri bloğu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi. `foreach` Deyimi bu türlerde sınırlı değildir ve aşağıdaki koşulları karşılayan herhangi bir türde bir örneğine uygulanabilir:

- Parametresiz ortak olan `GetEnumerator` yöntemi, dönüş türü olan sınıf, yapı veya arabirim türü
- dönüş türü `GetEnumerator` yöntemi ortak olan `Current` özelliği ve parametresiz ortak `MoveNext` yöntemi, dönüş türü olan <xref:System.Boolean>.

Bir oranda noktası içinde `foreach` deyimi bloğu, bölün dışında döngü kullanarak [sonu](break.md) deyimi ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) deyimi. Ayrıca çıkabilirsiniz bir `foreach` tarafından döngü [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.

## <a name="examples"></a>Örnekler

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek kullanımını gösterir `foreach` örneği deyimiyle <xref:System.Collections.Generic.List%601> uygulayan tür <xref:System.Collections.Generic.IEnumerable%601> arabirimi:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Sonraki örnek kullanır `foreach` örneği deyimiyle <xref:System.Span%601?displayProperty=nameWithType> arabirimlerden uygulamaz türü:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

C# ile 7.3, varsa başlayan Numaralandırıcının `Current` özelliği döndürür bir [başvuru dönüş değeri](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` burada `T` koleksiyon öğesi türü), yineleme değişkeni ile bildirebilir `ref` veya `ref readonly` değiştiricisi. Aşağıdaki örnek kullanan bir `ref` stackalloc dizideki her öğe değerini ayarlamak için yineleme değişkeni. `ref readonly` Sürüm tekrarlanan tüm değerleri yazdırmak için koleksiyonu. `readonly` Bildirimini örtük bir yerel değişken bildirimi kullanır. Örtük değişken bildirimleri ile birlikte kullanılabilir `ref` veya `ref readonly` açıkça gibi bildirimleri yazılan değişken bildirimleri.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

[Foreach deyimi (C# dil belirtimi)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[Dizilerle foreach kullanma](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[Yineleme Deyimleri](iteration-statements.md)  
[C# Anahtar Sözcükleri](index.md)  
[C# başvurusu](../index.md)  
[C# Programlama Kılavuzu](../../programming-guide/index.md)  
