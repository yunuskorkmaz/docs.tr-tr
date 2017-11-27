---
title: C# ifadelerinin - C# dili turu
description: "Using deyimleri C# programının eylemler oluşturun"
keywords: ".NET, csharp, deyimleri, sözdizimi"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 99ec2489daf89926da9b8c4e148965412826a8a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="statements"></a>Deyimler

Bir program Eylemler Java'daki *deyimleri*. C# birkaç farklı türde bir dizi katıştırılmış ifadeler bakımından tanımlanmış ifadeleri destekler.

A *blok* bağlamlarda yazılması için birden çok deyime burada tek bir deyimde izin verir. Bir blok arasında sınırlayıcıları yazılmış deyimleri listesini oluşur `{` ve `}`.

*Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.

*İfade deyimleri* ifadeleri değerlendirmek için kullanılır. Nesne kullanan ayırmaları deyimleri kullanılabilir ifadeler içeren yöntemi çağrılarını `new` işleç, kullanarak atamaları `=` ve bileşik atama işleçleri, kullanarakartırmaveazaltmaişlemleri`++`ve `--` işleçler ve `await` ifadeler.

*Seçim deyimleri* değerine göre bazı ifade yürütme için olası bilgilerinin sayısı birini seçmek için kullanılır. Bu gruba `if` ve `switch` deyimleri.

*Yineleme deyimleri* art arda katıştırılmış bir deyim yürütmek için kullanılır. Bu gruba `while`, `do`, `for`, ve `foreach` deyimleri.

*Atlama deyimleri* denetim aktarmak için kullanılır. Bu gruba `break`, `continue`, `goto`, `throw`, `return`, ve `yield` deyimleri.

`try`... `catch` deyimi bir blok yürütülmesi sırasında oluşan özel durumları yakalamak için kullanılır ve `try`... `finally` deyimi her zaman yürütülür sonlandırma kodu veya bir özel durum oluştu olup olmadığını belirtmek için kullanılır.

`checked` Ve `unchecked` deyimleri integral türü aritmetik işlemler ve dönüşümleri taşma denetimi bağlamı denetlemek için kullanılır.

`lock` Deyimi, belirli bir nesne için karşılıklı dışlama kilidi elde etmek, bir deyim yürütmek ve kilidi serbest için kullanılır.

`using` Deyimi bu kaynağını atma bir kaynağı edinmek ve bir deyim yürütmek için kullanılır.

Aşağıda, her biri için bir örnek sağlar ve kullanılabilir deyimleri türlerini listeler.

* Yerel değişken bildirimi:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Yerel sabit bildirimi:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* İfade deyimi:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if`bildirimi:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch`bildirimi:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while`bildirimi:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do`bildirimi:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for`bildirimi:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach`bildirimi:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break`bildirimi:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue`bildirimi:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto`bildirimi:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return`bildirimi:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield`bildirimi:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw`deyimleri ve `try` deyimleri:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked`ve `unchecked` deyimleri:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock`bildirimi:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using`bildirimi:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
[Önceki](expressions.md)
[sonraki](classes-and-objects.md)
