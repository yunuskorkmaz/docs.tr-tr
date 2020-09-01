---
description: Bağlamsal anahtar sözcük-C# başvurusu
title: Bağlamsal anahtar sözcük-C# başvurusu
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: bd3a7beeb7d3c4b62d6b70e2b1c6f38ab4b6804f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138221"
---
# <a name="when-c-reference"></a>ne zaman (C# Başvurusu)

`when`Aşağıdaki bağlamlarda bir filtre koşulu belirtmek için bağlamsal anahtar sözcüğünü kullanabilirsiniz:

- `catch` [Try/catch](try-catch.md) veya [try/catch/finally](try-catch-finally.md) bloğunun bildiriminde.
- `case`Bir [Switch](switch.md) ifadesinin etiketinde.
- [ `switch` İfadesi](../operators/switch-expression.md).

## <a name="when-in-a-catch-statement"></a>`when` bir `catch` ifadede

C# 6 ' dan itibaren, `when` `catch` belirli bir özel durumun yürütülmesi için doğru olması gereken bir koşul belirtmek üzere bir bildirimde kullanılabilir. Sözdizimi şöyledir:

```csharp
catch (ExceptionType [e]) when (expr)
```

Burada *Expr* , Boolean değer değerlendiren bir ifadedir. Döndürürse `true` , özel durum işleyicisi yürütülür; varsa, yapmaz `false` .

Aşağıdaki örnek, `when` <xref:System.Net.Http.HttpRequestException> özel durum iletisinin metnine bağlı olarak işleyicileri koşullu olarak yürütmek için anahtar sözcüğünü kullanır.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`when` bir `switch` ifadede

C# 7,0 ' den başlayarak `case` etiketlerin artık birbirini dışlamalı olması gerekmez ve `case` etiketlerin bir bildirimde görünme sırası `switch` hangi anahtar bloğunun çalıştırılacağını tespit edebilir. `when`Anahtar sözcüğü, ilişkili Case etiketinin doğru olmasına neden olan bir filtre koşulunu belirtmek için kullanılabilir ve yalnızca filtre koşulu da geçerlidir. Sözdizimi şöyledir:

```csharp
case (expr) when (when-condition):
```

Burada *Expr* , Match ifadesiyle karşılaştırılan sabit bir model veya tür deseninin olduğu *durumlarda-Condition* herhangi bir Boolean ifadedir.

Aşağıdaki örnek, `when` `Shape` bir alanı sıfır olan nesneleri test etmek ve `Shape` sıfırdan büyük bir alana sahip çeşitli nesneleri test etmek için anahtar sözcüğünü kullanır.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [switch deyimi](switch.md)
- [Try/Catch ekstresi](try-catch.md)
- [try/catch/finally ekstresi](try-catch-finally.md)
