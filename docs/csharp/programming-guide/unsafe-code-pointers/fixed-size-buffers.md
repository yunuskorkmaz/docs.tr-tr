---
title: Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9158550885ea0a95a56f318362b21db48e648234
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)

C# ' ta kullanabileceğiniz [sabit](../../language-reference/keywords/fixed-statement.md) ifadesi bir veri yapısında bir sabit boyutlu bir diziye sahip bir arabellek oluşturun. Bu veri kaynakları birlikte çalışma yöntemlerini diğer diller veya platformları yazdığınızda, sabit boyutlu arabellekler yararlı olur. Sabit dizi öznitelik ya da normal Yapı üyeleri için izin verilen değiştiricileri alabilir. Yalnızca dizi türü olmalıdır kısıtlamadır `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, veya `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Açıklamalar

Güvenli kodda bir dizi içeren bir C# yapı dizi öğeleri içermiyor. Bunun yerine, yapı öğeleri bir başvuru içeriyor. İçinde sabit boyutlu bir dizi eklenebilir bir [yapısı](../../language-reference/keywords/struct.md) içinde kullanıldığında bir [güvensiz](../../language-reference/keywords/unsafe.md) kod bloğu.

Aşağıdaki `struct` boyutu 8 bayt'tır. `pathName` Dizidir başvuru:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

A `struct` güvenli olmayan kod katıştırılmış bir dizide içerebilir. Aşağıdaki örnekte, `fixedBuffer` dizi sabit bir boyuta sahiptir. Kullandığınız bir `fixed` deyimi ilk öğe için bir işaretçi oluşturun. Dizideki öğeler bu işaretçinin erişebilirsiniz. `fixed` Deyimi PIN'ler `fixedBuffer` bellekte belirli bir konuma örnek alanı.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

128 öğe boyutunu `char` 256 baytı dizisidir. Boyutu sabit [char](../../language-reference/keywords/char.md) arabellekleri her zaman karakter kodlama bağımsız olarak, her iki byte uygulamanız. Bu bile zaman char arabellekleri API yöntemlerini veya yapılar ile sıralanmış geçerlidir `CharSet = CharSet.Auto` veya `CharSet = CharSet.Ansi`. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.

Önceki örnekte erişme gösterir `fixed` C# ile 7.3 itibaren kullanılabilir sabitleme, olmadan alanları...

Başka bir ortak sabit boyutlu dizi [bool](../../language-reference/keywords/bool.md) dizi. Öğeleri bir `bool` dizi her zaman bir bayt boyutunda. `bool` diziler bit dizileri veya arabelleklerinin oluşturmak için uygun değildir.

> [!NOTE]
> Kullanılarak oluşturulan bellek dışında [stackalloc](../../language-reference/keywords/stackalloc.md), C# Derleyici ve ortak dil çalışma zamanı (CLR) tüm güvenlik arabellek taşması denetimlerini gerçekleştirmeyin. Tüm güvenli olmayan kod ile dikkatli olarak.

Güvenli olmayan arabellekler normal diziler de aşağıdaki yollarla farklılık gösterir:

- Bu gibi durumlarda, güvenli olmayan arabellekler yalnızca güvensiz bir bağlamda kullanabilirsiniz.
- Güvenli olmayan arabellekler her zaman vektörlerinin ya da tek boyutlu diziler olur.
- Dizi bildirimi gibi bir sayı bulunması `char id[8]`. Kullanamazsınız `char id[]`.
- Güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda yapılar örneği alanları olabilir.

## <a name="see-also"></a>Ayrıca Bkz.

[C# Programlama Kılavuzu](../index.md)  
[Güvenli Olmayan Kod ve İşaretçiler](index.md)  
[fixed Deyimi](../../language-reference/keywords/fixed-statement.md)  
[Birlikte çalışabilirlik](../interop/index.md)
