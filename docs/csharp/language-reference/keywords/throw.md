---
description: throw-C# başvurusu
title: throw-C# başvurusu
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 4cad4810b89f976f92ce576917feb2398acce636
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142043"
---
# <a name="throw-c-reference"></a>throw (C# Başvurusu)

Programın yürütülmesi sırasında bir özel durumun oluşumunu bildirir.  
  
## <a name="remarks"></a>Açıklamalar

Sözdizimi şöyledir `throw` :

```csharp
throw [e];
```

Burada `e` türetilmiş bir sınıfın örneğidir <xref:System.Exception?displayProperty=nameWithType> . Aşağıdaki örnek, `throw` <xref:System.IndexOutOfRangeException> adlı bir metoda geçirilen bağımsız değişken `GetNumber` iç dizinin geçerli bir dizinine karşılık gelmiyorsa bir oluşturmak için ifadesini kullanır.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Yöntem çağıranları, sonra `try-catch` `try-catch-finally` oluşturulan özel durumu işlemek için bir veya bloğu kullanır. Aşağıdaki örnek, yöntemi tarafından oluşturulan özel durumu işler `GetNumber` .

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Özel durum yeniden oluşturuluyor

`throw` , `catch` bir blokta işlenen bir özel durumu yeniden oluşturmak için bir blokta da kullanılabilir `catch` .  Bu durumda, `throw` bir özel durum işleneni almaz. Bir yöntem çağıran bir bağımsız değişkende diğer bir kitaplık yöntemine geçtiğinde ve kitaplık yöntemi çağırana geçirilmesi gereken bir özel durum oluşturduğunda, en çok yararlı olur. Örneğin, aşağıdaki örnek, <xref:System.NullReferenceException> başlatılmamış bir dizenin ilk karakterini almaya çalışırken oluşturulan bir öğesini yeniden atar.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Ayrıca, `throw e` `catch` çağrıyı yapana geçirdiğiniz yeni bir özel durum oluşturmak için bir blokta söz dizimini kullanabilirsiniz. Bu durumda, özelliğinden erişilebilen özgün özel durumun yığın izlemesi <xref:System.Exception.StackTrace> korunmaz.

## <a name="the-throw-expression"></a>`throw`İfade

C# 7,0 ' den itibaren bir deyim ve `throw` deyim olarak kullanılabilir. Bu, daha önce desteklenmeyen bağlamlarda bir özel durumun oluşturulmasına olanak sağlar. Bu güncelleştirmeler şunlardır:

- [koşullu işleç](../operators/conditional-operator.md). Aşağıdaki örnek, bir `throw` <xref:System.ArgumentException> Yöntem boş bir dize dizisi geçirtiyse, oluşturmak için bir ifade kullanır. C# 7,0 ' den önce, bu mantığın bir bildirimde görünmesi gerekir `if` / `else` .

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [null birleşim işleci](../operators/null-coalescing-operator.md). Aşağıdaki örnekte bir `throw` ifade, bir özelliğe atanmış dize ise bir özel durum oluşturmak için null birleşim işleciyle birlikte kullanılır `Name` `null` .

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- ifade-Bodied [lambda](../operators/lambda-expressions.md) veya yöntem. Aşağıdaki örnek, bir <xref:System.InvalidCastException> değere dönüştürme desteklenmediğinden bir ifade-Bodied yöntemi gösterir <xref:System.DateTime> .

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [C# anahtar sözcükleri](index.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
