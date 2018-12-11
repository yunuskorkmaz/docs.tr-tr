---
title: C#Deyimleri - Turu C# dil
description: Eylemler, oluşturduğunuz bir C# deyimleri kullanarak program
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 75f6c7bb29af7f9c809c5278c97d21683166a8e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154300"
---
# <a name="statements"></a>Deyimler

Bir programın eylemleri kullanılarak ifade edilir *deyimleri*. C# ifadeleri açısından katıştırılmış deyimi bir dizi tanımlanmış birkaç farklı türde destekler.

A *blok* bağlamlarda yazılacak birden çok deyime burada tek bir deyimde izin verir. Sınırlayıcılar yazılan deyimlerin listesini bir blok oluşan `{` ve `}`.

*Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.

*İfade deyimleri* ifadeler değerlendirilir. Deyimleri kullanılabilir ifadeler, yöntem çağrılarını içeren nesne ayırmaları kullanarak `new` işleç, atamaları kullanarak `=` ve bileşik atama işleçleri, artırma ve azaltma işlemlerini kullanarak`++`ve `--` işleçler ve `await` ifadeler.

*Seçim deyimleri* olası deyimleri yürütme bazı ifadesinin değerine göre bir dizi birini seçmek için kullanılır. Bu gruba `if` ve `switch` deyimleri.

*Yineleme deyimleri* sürekli bir katıştırılmış deyimi yürütmek için kullanılır. Bu gruba `while`, `do`, `for`, ve `foreach` deyimleri.

*Atlama deyimleri* denetim aktarmak için kullanılır. Bu gruba `break`, `continue`, `goto`, `throw`, `return`, ve `yield` deyimleri.

`try`... `catch` deyimi, bir blok yürütülmesi sırasında oluşan özel durumları yakalamak için kullanılır ve `try`... `finally` deyimi veya bir özel durum oluştu olup olmadığını her zaman yürütülür, sonlandırma kodu belirtmek için kullanılır.

`checked` Ve `unchecked` ifadeler Tamsayı türünde aritmetik işlemler ve dönüştürmeler için taşma denetimi bağlamını denetlemek için kullanılır.

`lock` Deyimi belirli bir nesne için karşılıklı dışlama kilidini almak, bir deyimi yürütün ve sonra kilidi için kullanılır.

`using` Deyimi bir kaynağı almak, bir deyimi yürütün ve sonra o kaynağını atma için kullanılır.

Aşağıda, her biri için bir örnek sağlar ve kullanılabilir deyimleri türlerini listeler.

* Yerel değişken bildirimi:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Yerel sabit bildiriminde:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* İfade deyimi:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if` deyimi:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch` deyimi:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while` deyimi:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do` deyimi:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for` deyimi:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach` deyimi:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break` deyimi:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue` deyimi:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto` deyimi:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return` deyimi:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield` deyimi:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw` deyimleri ve `try` ifadeleri:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked` ve `unchecked` ifadeleri:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock` deyimi:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using` deyimi:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Önceki](expressions.md)
>[İleri](classes-and-objects.md)