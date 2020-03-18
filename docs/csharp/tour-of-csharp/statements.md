---
title: C# Deyimleri - C# dilinde bir tur
description: İfadeleri kullanarak bir C# programının eylemlerini oluşturursunuz
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159110"
---
# <a name="statements"></a>Deyimler

Bir programın eylemleri *ifadeleri*kullanılarak ifade edilir. C#, bir dizi katıştırılmış deyim ler açısından tanımlanan birkaç farklı ifade yi destekler.

*Blok,* tek bir deyimin izin verildiği bağlamlarda birden çok deyimin yazılmasına izin verir. Blok, sınır layıcılar `{` ve `}`.

*Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.

*İfade ifadeleri* ifadeleri değerlendirmek için kullanılır. Deyim olarak kullanılabilecek ifadeler yöntem çağrılarını, `new` işleci kullanan nesne ayırmaları, `=` kullanılan atamaları ve bileşik atama işleçlerini, `++` ve `--` işleçleri ve `await` ifadeleri kullanarak artırma ve decrement işlemlerini içerir.

*Seçim deyimleri,* bazı ifadelerin değerine bağlı olarak yürütme için olası ifadelerden birini seçmek için kullanılır. Bu grup `if` ve `switch` ifadeler içerir.

*Yineleme deyimleri,* katıştırılmış bir deyimi tekrar tekrar yürütmek için kullanılır. Bu grup `while`, `do` `for`, `foreach` ve ifadeler içerir.

*Atlama deyimleri* denetimi aktarmak için kullanılır. Bu grup `break`, `continue` `goto`, `throw` `return`, `yield` , , ve ifadeleri içerir.

Bu `try`... `catch` deyimi bir blok yürütülmesi sırasında meydana gelen özel durumları `try`yakalamak için kullanılır ve ... `finally` deyimi, bir özel durum oluştu veya değil, her zaman yürütülen sonlandırma kodunu belirtmek için kullanılır.

Ve `checked` `unchecked` deyimler, integral türü aritmetik işlemler ve dönüşümler için taşma denetimi bağlamını denetlemek için kullanılır.

İfade, `lock` belirli bir nesne için karşılıklı dışlama kilidi elde etmek, bir deyimi yürütmek ve kilidi serbest bırakmak için kullanılır.

Deyim, `using` bir kaynak elde etmek, bir deyim yürütmek ve sonra bu kaynağı elden çıkarmak için kullanılır.

Aşağıda kullanılabilecek deyim türlerini listeler ve her biri için bir örnek sağlar.

* Yerel değişken bildirimi:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Yerel sabit bildirim:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* İfade deyimi:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if`Deyim:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch`Deyim:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while`Deyim:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do`Deyim:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for`Deyim:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach`Deyim:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break`Deyim:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue`Deyim:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto`Deyim:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return`Deyim:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield`Deyim:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw`ifadeler `try` ve ifadeler:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked`ve `unchecked` ifadeler:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock`Deyim:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using`Deyim:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Önceki](expressions.md)
>[Sonraki](classes-and-objects.md)
