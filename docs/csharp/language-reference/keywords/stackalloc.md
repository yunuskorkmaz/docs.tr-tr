---
title: stackalloc (C# Başvurusu)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 5926550eea1f5a2f8fb74645f22ca54c2bed3136
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508586"
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# Başvurusu)
`stackalloc` Anahtar sözcüğü bir güvenli olmayan kod bağlamında bir yığında bellek bloğu ayırmak için kullanılır.

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a>Açıklamalar

Anahtar sözcüğü, yalnızca yerel değişken başlatıcı içinde geçerli değil. Aşağıdaki kod derleyici hatasına neden olur.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

C# 7.3 ile başlayarak, dizi Başlatıcı sözdizimi kullanabilirsiniz `stackalloc` dizileri. Aşağıdaki bildirimleri tamsayı değerleri olan üç öğe olan bir dizi bildirmek `1`, `2`, ve `3`:

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

İşaretçi türleri dahil olduğundan `stackalloc` gerektiren bir [güvenli](unsafe.md) bağlamı. Daha fazla bilgi için [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md) 

`stackalloc` benzer [_alloca](/cpp/c-runtime-library/reference/alloca) C Çalışma Zamanı Kitaplığı'nda.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, hesaplar ve ilk 20 sayıları Fibonacci sırayla görüntüler. Her bir sayının, önceki iki sayının toplamıdır. Kodda, 20 öğe türü içerecek şekilde yeterli boyutunda bellek bloğu `int` yığın yığında ayrılır. Blok adresini işaretçide depolanan `fib`. Bu bellek tabi atık koleksiyonu olması gerekmez ve bu nedenle sabitlenmiş gerekmez (kullanarak [sabit](fixed-statement.md)). Bellek bloğu ömrünü tanımlayan yöntemin ömrünü sınırlıdır. Yöntem döndürmeden önce belleği serbest bırakılamıyor.

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

Aşağıdaki örnek başlatır bir `stackalloc` her öğe için bir bit maskesi olan bir bit tamsayı dizisi ayarlayın. Bu yeni Başlatıcı sözdizimi C# 7.3 itibaren kullanıma gösterir:

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Güvenlik

Güvenli olmayan kod güvenli alternatifler daha az güvenlidir. Ancak, kullanımını `stackalloc` otomatik olarak ortak dil çalışma zamanı (CLR) arabellek taşması algılama özelliklerini etkinleştirir. İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.

## <a name="c-language-specification"></a>C# Dil Belirtimi
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
