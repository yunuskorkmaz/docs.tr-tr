---
title: C#Deyimler- C# dilin turu
description: Deyimleri kullanarak bir C# programın eylemlerini oluşturun
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159110"
---
# <a name="statements"></a>Deyimler

Bir programın eylemleri *deyimler*kullanılarak ifade edilir. C#, birden çok farklı türde deyimi destekler, bu sayı katıştırılmış deyimler bakımından tanımlanır.

Bir *blok* , tek bir ifadeye izin verilen bağlamlarda birden çok deyimin yazılmasına izin verir. Bir blok `{` ve `}`sınırlayıcıları arasına yazılan deyimler listesinden oluşur.

*Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.

*İfade deyimleri* , ifadeleri değerlendirmek için kullanılır. Deyimler olarak kullanılabilecek ifadeler, `new` işleci kullanılarak nesne ayırmaları, `=` ve bileşik atama işleçleri kullanılarak atamalar, `++` ve `--` işleçlerini ve `await` ifadelerini kullanarak işlemleri artırma ve azaltma işlemlerini içerir.

*Seçim deyimleri* , bazı deyimlerin değerine göre yürütme için bir dizi olası deyimden birini seçmek için kullanılır. Bu grup `if` ve `switch` deyimlerini içerir.

*Yineleme deyimleri* , art arda gömülü bir deyimi yürütmek için kullanılır. Bu grup `while`, `do`, `for`ve `foreach` deyimlerini içerir.

*Sıçrama deyimleri* , denetimi aktarmak için kullanılır. Bu grup `break`, `continue`, `goto`, `throw`, `return`ve `yield` deyimlerini içerir.

`try`...`catch` deyimleri, bir bloğun yürütülmesi sırasında oluşan özel durumları yakalamak için kullanılır ve bir özel durumun gerçekleşmediği, her zaman yürütülen sonlandırma kodunu belirtmek için `try`...`finally` deyimleri kullanılır.

`checked` ve `unchecked` deyimleri, tam sayı türü aritmetik işlemler ve dönüştürmeler için taşma denetimi bağlamını denetlemek üzere kullanılır.

`lock` deyimleri, belirli bir nesne için karşılıklı dışlama kilidini almak, bir ifadeyi yürütmek ve sonra kilidi serbest bırakmak için kullanılır.

`using` deyimleri, kaynak almak, bir ifadeyi yürütmek ve ardından bu kaynağı atmak için kullanılır.

Aşağıdakiler, kullanılabilecek deyimlerin türlerini listeler ve her biri için bir örnek sağlar.

* Yerel değişken bildirimi:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Yerel sabit bildirimi:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* İfade deyimi:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if` ekstresi:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch` ekstresi:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while` ekstresi:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do` ekstresi:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for` ekstresi:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach` ekstresi:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break` ekstresi:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue` ekstresi:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto` ekstresi:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return` ekstresi:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield` ekstresi:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw` deyimleri ve `try` deyimleri:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked` ve `unchecked` deyimleri:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock` ekstresi:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using` ekstresi:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Önceki](expressions.md)
>[İleri](classes-and-objects.md)
