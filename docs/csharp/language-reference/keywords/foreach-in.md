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
ms.openlocfilehash: 3fbaacb96be2714aaff49679836e5d2d4a3783da
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422476"
---
# <a name="foreach-in-c-reference"></a>foreach, (C# Başvurusu)

`foreach` Deyimi uygulayan türü örneğinde bir deyimi veya bir her öğe için bir deyimler bloğunu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi. `foreach` Deyimi bu türleri için sınırlı değildir ve aşağıdaki koşulları karşılayan herhangi bir türde bir örneğine uygulanabilir:

- Genel parametresiz `GetEnumerator` yöntemi, dönüş türü olan sınıf, yapı veya arabirim türü
- dönüş türünü `GetEnumerator` yöntemi ortak sahip `Current` özelliği ve parametresiz public `MoveNext` yöntemi, dönüş türü olan <xref:System.Boolean>.

C# 7.3, ile başlayarak Numaralandırıcı `Current` özelliği döndürür bir [başvuru dönüş değeri](ref.md#reference-return-values) (`ref T` burada `T` koleksiyon öğesi türü), yineleme değişkeni ile bildirebilirsiniz `ref` veya `ref readonly` değiştiricisi.

Herhangi bir anda işaret içinde `foreach` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi veya bir sonraki yinelemesine kullanarak adım [devam](continue.md) deyimi. Ayrıca çıkış bir `foreach` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.

Varsa `foreach` deyimi uygulanan `null`, <xref:System.NullReferenceException> oluşturulur. Kaynak koleksiyonunu `foreach` boş deyim gövdesi `foreach` döngü değil yürütülen ve atlandı.

## <a name="examples"></a>Örnekler

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, kullanımını gösterir. `foreach` örneği deyimiyle <xref:System.Collections.Generic.List%601> uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> arabirimi:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Sonraki örnekte `foreach` örneği deyimiyle <xref:System.Span%601?displayProperty=nameWithType> arabirimlerden uygulamayan türü:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Aşağıdaki örnekte bir `ref` bir stackalloc dizideki her öğenin değerini ayarlamak için yineleme değişkeni. `ref readonly` Sürüm tüm değerleri yazdırmak için koleksiyon yinelenir. `readonly` Bildirimi örtük bir yerel değişken bildirimini kullanır. Örtük değişken bildirimleri ile birlikte kullanılabilir `ref` veya `ref readonly` açıkça mümkün olduğunca bildirimleri, yazdığınız değişken bildirimleri.

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [foreach deyimi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Dizilerle foreach kullanma](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [For deyimi](for.md)
