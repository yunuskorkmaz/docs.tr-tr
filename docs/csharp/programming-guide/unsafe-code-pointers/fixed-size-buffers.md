---
title: Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 0691c33b551e39b2384950cfcd0be6e8a3a29cee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506907"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)

C# ' ta kullanabileceğiniz [sabit](../../language-reference/keywords/fixed-statement.md) deyimini bir sabit boyutlu diziye bir veri yapısına sahip bir arabellek oluşturun. Sabit boyutlu arabellekler, yöntemler diğer dillerde veya platformlarda veri kaynaklarıyla bu birlikte çalışma yazmak olduğunda yararlıdır. Sabit dizi herhangi bir öznitelik veya normal Yapı üyeleri için izin verilen değiştiriciler alabilir. Yalnızca dizi türü olmalıdır kısıtlamadır `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, veya `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Açıklamalar

Güvenli kod içinde bir dizi içeren bir C# yapı dizi öğeleri içermiyor. Bunun yerine, yapı öğeleri bir başvuru içeriyor. İçinde sabit boyutlu bir dizi katıştırabilirsiniz bir [yapı](../../language-reference/keywords/struct.md) içinde kullanıldığında bir [güvenli](../../language-reference/keywords/unsafe.md) kod bloğu.

Aşağıdaki `struct` 8 bayt cinsinden boyutu. `pathName` Başvuru dizisidir:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

A `struct` güvenli olmayan kod içinde gömülü bir dizi içerebilir. Aşağıdaki örnekte, `fixedBuffer` dizi sabit bir boyuta sahiptir. Kullandığınız bir `fixed` ilk öğeye bir işaretçi kurmak için deyimi. Bu işaretçiyle dizinin öğeleri eriştiğinize. `fixed` Deyimi PIN'ler `fixedBuffer` bellekte belirli bir konuma örnek alanı.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

128 öğe `char` 256 bayt dizisidir. Boyutu sabit [char](../../language-reference/keywords/char.md) arabellekler her zaman, bağımsız olarak kodlama karakter başına iki bayttan yönlendirir. Bu da zaman char arabellekler API yöntemleri veya yapılar ile sıralanmış geçerlidir `CharSet = CharSet.Auto` veya `CharSet = CharSet.Ansi`. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.

Yukarıdaki örnekte erişme gösterir `fixed` ile C# 7.3'den itibaren kullanılabilmektedir sabitleme, olmadan alanları...

Başka bir ortak sabit boyutlu dizi [bool](../../language-reference/keywords/bool.md) dizisi. Öğeleri bir `bool` dizi her zaman tek bir bayt boyutunda. `bool` diziler bit diziler veya arabellekler oluşturmak için uygun değildir.

> [!NOTE]
> Kullanılarak oluşturulan bellek dışında [stackalloc](../../language-reference/keywords/stackalloc.md), C# Derleyici ve ortak dil çalışma zamanı (CLR) herhangi bir güvenlik arabellek taşma denetimi gerçekleştirmeyin. Tüm güvenli olmayan kod gibi dikkatli kullanın.

Güvenli olmayan arabellekler normal dizilerden şu bakımlardan ayrılır:

- Bu gibi durumlarda, güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda kullanabilirsiniz.
- Güvenli olmayan arabellekler, vektör veya tek boyutlu diziler her zaman olur.
- Dizi bildirimi bir sayı gibi bulunması `char id[8]`. Kullanamazsınız `char id[]`.
- Güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda yapılar örnek alanları olabilir.

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../index.md)  
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)  
- [fixed Deyimi](../../language-reference/keywords/fixed-statement.md)  
- [Birlikte çalışabilirlik](../interop/index.md)
