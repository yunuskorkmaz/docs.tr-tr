---
title: throw- C# Reference
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 04d3138e3390627355b4b2d4e25c6b00248cec1a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713059"
---
# <a name="throw-c-reference"></a>throw (C# Başvurusu)

Programın yürütülmesi sırasında bir özel durumun oluşumunu bildirir.  
  
## <a name="remarks"></a>Açıklamalar

`throw` sözdizimi şöyledir:

```csharp
throw [e];
```

Burada `e` <xref:System.Exception?displayProperty=nameWithType>türetilen bir sınıfın örneğidir. Aşağıdaki örnek, `GetNumber` adlı bir metoda geçirilen bağımsız değişken iç dizinin geçerli bir dizinine karşılık gelmiyorsa, bir <xref:System.IndexOutOfRangeException> oluşturmak için `throw` ifadesini kullanır.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Yöntem çağıranları, sonra oluşturulan özel durumu işlemek için bir `try-catch` veya `try-catch-finally` bloğu kullanır. Aşağıdaki örnek, `GetNumber` metodu tarafından oluşturulan özel durumu işler.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Özel durum yeniden oluşturuluyor

`throw`, bir `catch` bloğunda işlenen bir özel durumu yeniden oluşturmak için bir `catch` bloğunda de kullanılabilir.  Bu durumda, `throw` bir özel durum işleneni almaz. Bir yöntem çağıran bir bağımsız değişkende diğer bir kitaplık yöntemine geçtiğinde ve kitaplık yöntemi çağırana geçirilmesi gereken bir özel durum oluşturduğunda, en çok yararlı olur. Örneğin, aşağıdaki örnek, başlatılmamış bir dizenin ilk karakterini almaya çalışırken oluşturulan bir <xref:System.NullReferenceException> yeniden oluşturur.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Çağırana geçirdiğiniz yeni bir özel durum oluşturmak için bir `catch` bloğunda `throw e` sözdizimini de kullanabilirsiniz. Bu durumda, <xref:System.Exception.StackTrace> özelliğinden erişilebilen özgün özel durumun yığın izlemesi korunmaz.

## <a name="the-throw-expression"></a>`throw` ifadesi

7,0 ile C# başlayarak, `throw` bir deyim ve deyim olarak kullanılabilir. Bu, daha önce desteklenmeyen bağlamlarda bir özel durumun oluşturulmasına olanak sağlar. Bu güncelleştirmeler şunlardır:

- [koşullu işleç](../operators/conditional-operator.md). Aşağıdaki örnek, bir yöntem boş bir dize dizisi geçirtiyse bir <xref:System.ArgumentException> oluşturmak için `throw` ifadesini kullanır. 7,0 C# ' den önce, bu mantığın bir `if`/`else` ifadesinde görünmesi gerekir.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [null birleşim işleci](../operators/null-coalescing-operator.md). Aşağıdaki örnekte, bir `Name` özelliğine atanan dize `null`bir özel durum oluşturmak için null birleşim işleci ile bir `throw` ifadesi kullanılır.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- ifade-Bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) veya yöntem. Aşağıdaki örnek, bir <xref:System.DateTime> değerine dönüştürme desteklenmediğinden bir <xref:System.InvalidCastException> oluşturan ifade-Bodied yöntemini gösterir.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [C# Anahtar Sözcükleri](index.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
