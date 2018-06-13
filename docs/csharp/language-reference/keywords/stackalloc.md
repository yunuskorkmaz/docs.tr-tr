---
title: stackalloc (C# Başvurusu)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 905873cf7f576ff35a9bc1c182ce7ebe17920288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269174"
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# Başvurusu)
`stackalloc` Anahtar sözcüğü bir güvenli olmayan kod bağlamında kullanılan yığında bir bellek bloğu ayrılamadı.

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a>Açıklamalar

Anahtar sözcüğü yalnızca yerel değişken başlatıcıları içinde geçerli değil. Aşağıdaki kod derleyici hataları neden olur.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

C# 7.3 ile başlayarak, dizi Başlatıcısı sözdizimi için kullanabileceğiniz `stackalloc` dizileri. Değerleri tamsayı olan üç öğeye sahip bir dizi aşağıdaki bildirimlerini bildirme `1`, `2`, ve `3`:

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

İşaretçi türleri dahil olduğundan `stackalloc` gerektiren bir [güvensiz](unsafe.md) bağlamı. Daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md) 

`stackalloc` benzer [_alloca](/cpp/c-runtime-library/reference/alloca) C Çalışma Zamanı Kitaplığı'nda.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, hesaplar ve ilk 20 sayıları Fibonacci sırada görüntüler. Her numarası önceki sayılarının toplamıdır. Kodda, türündeki 20 öğeler içerecek şekilde yeterli boyutunda bellek bloğu `int` yığın yığında ayrılmış. Blok adresini işaretçinin depolanan `fib`. Bu bellek çöp toplama tabi değildir ve bu nedenle sabitlenmiş olmak zorunda değildir (kullanarak [sabit](fixed-statement.md)). Bellek bloğu ömrü tanımladığı yöntemi için kullanım ömrü sınırlıdır. Yöntem döndürmeden önce bellek bırakılamıyor.

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

Aşağıdaki örnek başlatır bir `stackalloc` dizisi bir bit ile bir bit maskesi için her bir öğe ayarlayın. C# 7.3 içinde başlayarak kullanılabilir yeni Başlatıcısı sözdizimi gösterilmektedir:

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Güvenlik

Güvenli olmayan kod güvenli alternatifler daha az güvenlidir. Ancak, kullanımını `stackalloc` ortak dil çalışma zamanı (CLR) arabellek taşması algılama özellikleri otomatik olarak etkinleştirir. İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.

## <a name="c-language-specification"></a>C# Dil Belirtimi
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
