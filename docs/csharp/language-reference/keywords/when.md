---
title: zaman (C# Başvurusu)
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 3168cf620eb3aaf206afbe5bc2efc297832503ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
 # <a name="when-c-reference"></a>zaman (C# Başvurusu)

Kullanabileceğiniz `when` bağlamsal anahtar sözcüğü bir filtre koşulu iki bağlamlarda belirtmek için:

- İçinde `catch` deyiminin bir [try/catch](try-catch.md) veya [try/catch/finally](try-catch-finally.md) bloğu.
- İçinde `case` etiketini bir [geçiş](switch.md) deyimi.

## <a name="when-in-a-catch-statement"></a>`when` içinde bir `catch` deyimi

C# 6 ile başlayarak `When` kullanılabilir bir `catch` deyimi yürütmek belirli bir özel durum işleyicisi için doğru bir koşulu belirtin. Sözdizimi aşağıdaki gibidir:

```csharp
catch ExceptionType [e] when (expr)
```
Burada *expr* bir Boole değeri veren ifade. Döndürürse `true`, özel durum işleyici; varsa yürütür `false`, yok. 

Aşağıdaki örnek kullanır `when` koşullu işleyicileri yürütülecek anahtar sözcüğü bir <xref:System.Net.Http.HttpRequestException> özel durum iletisi metnin bağlı olarak.

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a>`when` içinde bir `switch` deyimi

C# 7.0 ile başlayan `case` etiketleri artık olması birbirini dışlayan ve hangi sırayla `case` etiketlerinin görünür bir `switch` deyimi, hangi anahtar bloğu belirleyebilir yürütür. `when` Anahtar sözcüğü yalnızca filtre koşulu da true ise true olarak ilişkili servis talebi etiketini neden olan bir filtre koşulu belirtmek için kullanılabilir. Sözdizimi aşağıdaki gibidir:

```csharp
case (expr) when (when-condition):
```
Burada *expr* bir sabit düzeni ya da eşleşme ifadesi için karşılaştırma türü düzeni ve *olduğunda koşulu* herhangi Boole ifadesi. 

Aşağıdaki örnek kullanır `when` sınamak için anahtar sözcüğü `Shape` çeşitli için test etmek için sıfır de alanı nesneleri `Shape` sıfırdan büyük bir alana sahip nesneleri. 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a>Ayrıca bkz. 
  [Switch deyimi](switch.md)  
  [try/catch deyimi](try-catch.md)  
  [try/catch/finally ifadesi](try-catch-finally.md) 

