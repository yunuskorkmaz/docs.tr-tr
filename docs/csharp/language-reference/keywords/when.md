---
title: Bağlamsal anahtar sözcük C# referansı
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712838"
---
# <a name="when-c-reference"></a>ne zamanC# (başvuru)

İki bağlamda bir filtre koşulu belirtmek için `when` bağlamsal anahtar sözcüğünü kullanabilirsiniz:

- [Try/catch](try-catch.md) veya [try/catch/finally](try-catch-finally.md) bloğunun `catch` bildiriminde.
- [Switch](switch.md) ifadesinin `case` etiketinde.

## <a name="when-in-a-catch-statement"></a>`catch` bildiriminde `when`

C# 6 ' dan itibaren, belirli bir özel durumun yürütülmesi için doğru olması gereken bir koşul belirtmek üzere bir `catch` bildiriminde `when` kullanılabilir. Sözdizimi şöyledir:

```csharp
catch (ExceptionType [e]) when (expr)
```

Burada *Expr* , Boolean değer değerlendiren bir ifadedir. `true`döndürürse, özel durum işleyicisi yürütülür; `false`, değildir.

Aşağıdaki örnek, özel durum iletisinin metnine bağlı olarak bir <xref:System.Net.Http.HttpRequestException> için işleyicileri koşullu olarak yürütmek üzere `when` anahtar sözcüğünü kullanır.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`switch` bildiriminde `when`

7,0 ile C# başlayarak, artık `case` etiketlere gerek kalmaz ve `case` etiketlerin `switch` bir bildirimde görünme sırası, hangi anahtar bloğunun çalıştırılacağını tespit edebilir. `when` anahtar sözcüğü, ilişkili Case etiketinin doğru olmasına neden olan filtre koşulunu belirtmek için kullanılabilir. Sözdizimi şöyledir:

```csharp
case (expr) when (when-condition):
```

Burada *Expr* , Match ifadesiyle karşılaştırılan sabit bir model veya tür deseninin olduğu *durumlarda-Condition* herhangi bir Boolean ifadedir.

Aşağıdaki örnek, bir alanı sıfır olan `Shape` nesneleri test etmek için `when` anahtar sözcüğünü ve sıfırdan büyük bir alana sahip çeşitli `Shape` nesnelerini test etmek için kullanır.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Switch deyimleri](switch.md)
- [Try/Catch ekstresi](try-catch.md)
- [try/catch/finally ekstresi](try-catch-finally.md)
