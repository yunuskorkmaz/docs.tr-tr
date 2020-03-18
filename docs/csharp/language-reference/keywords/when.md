---
title: bağlamsal anahtar kelime - C# Reference
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712838"
---
# <a name="when-c-reference"></a>ne zaman (C# Reference)

`when` Bir filtre koşulunu iki bağlamda belirtmek için bağlamsal anahtar sözcüğü kullanabilirsiniz:

- Bir `catch` [deneyin / yakalamak](try-catch.md) veya denemek / yakalamak [/ nihayet](try-catch-finally.md) blok ifadesinde.
- Anahtar `case` deyiminin [switch](switch.md) etiketinde.

## <a name="when-in-a-catch-statement"></a>`when`bir `catch` açıklamada

C# 6 ile `when` başlayarak, `catch` belirli bir özel durum yürütmek için işleyici için doğru olması gereken bir koşul belirtmek için bir deyim kullanılabilir. Sözdizimi:

```csharp
catch (ExceptionType [e]) when (expr)
```

*expr* bir Boolean değerine değerlendiren bir ifadedir. Dönerse, `true`özel durum işleyicisi yürütür; eğer `false`, bu değil.

Aşağıdaki örnek, `when` özel durum iletisinin metnine <xref:System.Net.Http.HttpRequestException> bağlı olarak işleyicileri koşullu olarak yürütmek için anahtar sözcüğü kullanır.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`when`bir `switch` açıklamada

C# 7.0 ile `case` başlayarak, etiketlerin artık birbirini dışlayan `case` olması gerekmez `switch` ve bir deyimde etiketlerin görünme sırası hangi anahtar bloğunun yürütüleceğini belirleyebilir. Anahtar `when` kelime, yalnızca filtre koşulu da doğruysa ilişkili durum etiketinin doğru olmasını sağlayan bir filtre koşulu belirtmek için kullanılabilir. Sözdizimi:

```csharp
case (expr) when (when-condition):
```

*expr* eşleşme ifadesi ile karşılaştırıldığında sabit bir desen veya tür deseni nerede ve *ne zaman koşul* herhangi bir Boolean ifadedir.

Aşağıdaki `when` örnekte, sıfır lık `Shape` bir alana sahip nesneler için test etmek ve sıfırdan `Shape` büyük bir alana sahip çeşitli nesneleri sınamak için anahtar kelime kullanır.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [anahtar deyimi](switch.md)
- [try/catch deyimi](try-catch.md)
- [try/catch/finally deyimi](try-catch-finally.md)
