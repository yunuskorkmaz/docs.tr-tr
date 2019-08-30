---
title: throw- C# Reference
ms.custom: seodec18
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a9a235da06427e12bb5866a48f76f9c5896a572
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168742"
---
# <a name="throw-c-reference"></a>throw (C# Başvurusu)

Programın yürütülmesi sırasında bir özel durumun oluşumunu bildirir.  
  
## <a name="remarks"></a>Açıklamalar

Sözdizimi `throw` şöyledir:

```csharp
throw [e]
```

`e` burada<xref:System.Exception?displayProperty=nameWithType>türetilmiş bir sınıfın örneğidir. Aşağıdaki örnek, adlı `throw` `GetNumber` bir metoda geçirilen bağımsız değişken <xref:System.IndexOutOfRangeException> iç dizinin geçerli bir dizinine karşılık gelmiyorsa bir oluşturmak için ifadesini kullanır.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Yöntem çağıranları, sonra `try-catch` oluşturulan `try-catch-finally` özel durumu işlemek için bir veya bloğu kullanır. Aşağıdaki örnek, `GetNumber` yöntemi tarafından oluşturulan özel durumu işler.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Özel durum yeniden oluşturuluyor

`throw`, bir `catch` `catch` blokta işlenen bir özel durumu yeniden oluşturmak için bir blokta da kullanılabilir.  Bu durumda, `throw` bir özel durum işleneni almaz. Bir yöntem çağıran bir bağımsız değişkende diğer bir kitaplık yöntemine geçtiğinde ve kitaplık yöntemi çağırana geçirilmesi gereken bir özel durum oluşturduğunda, en çok yararlı olur. Örneğin, aşağıdaki örnek, başlatılmamış bir dizenin ilk karakterini <xref:System.NullReferenceException> almaya çalışırken oluşturulan bir öğesini yeniden atar.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Ayrıca, çağrıyı yapana geçirdiğiniz `throw e` yeni bir özel `catch` durum oluşturmak için bir blokta söz dizimini kullanabilirsiniz. Bu durumda, <xref:System.Exception.StackTrace> özelliğinden erişilebilen özgün özel durumun yığın izlemesi korunmaz.

## <a name="the-throw-expression"></a>`throw` İfade

7,0 ile C# başlayarak, `throw` bir deyim ve deyim olarak kullanılabilir. Bu, daha önce desteklenmeyen bağlamlarda bir özel durumun oluşturulmasına olanak sağlar. Bu güncelleştirmeler şunlardır:

- [koşullu işleç](../operators/conditional-operator.md). Aşağıdaki örnek, bir yöntem `throw` boş bir dize dizisi <xref:System.ArgumentException> geçirtiyse, oluşturmak için bir ifade kullanır. 7,0 C# öncesinde, bu mantığın bir `if` / `else` bildirimde görünmesi gerekir.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [null birleşim işleci](../operators/null-coalescing-operator.md). Aşağıdaki örnekte `throw` bir ifade, bir `Name` özelliğe atanmış dize ise `null`bir özel durum oluşturmak için null birleşim işleciyle birlikte kullanılır.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- ifade-Bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) veya yöntem. Aşağıdaki örnek, bir <xref:System.InvalidCastException> <xref:System.DateTime> değere dönüştürme desteklenmediğinden bir ifade-Bodied yöntemi gösterir.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a>C# dili belirtimi  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [C# Anahtar Sözcükleri](index.md)
- [Nasıl yapılır: Özel durumları açık olarak oluştur](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
