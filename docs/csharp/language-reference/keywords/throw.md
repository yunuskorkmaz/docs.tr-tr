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
ms.openlocfilehash: 1e3f9ff82bdc4f35232c4ea1162050e216a9cc21
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353425"
---
# <a name="throw-c-reference"></a>throw (C# Başvurusu)

Programın yürütülmesi sırasında bir özel durumun oluşumunu bildirir.  
  
## <a name="remarks"></a>Açıklamalar

@No__t-0 sözdizimi şöyledir:

```csharp
throw [e];
```

Burada `e` <xref:System.Exception?displayProperty=nameWithType> ' den türetilen bir sınıfın örneğidir. Aşağıdaki örnek, `GetNumber` adlı bir yönteme geçirilen bağımsız değişken iç dizinin geçerli bir dizinine karşılık gelmiyorsa bir <xref:System.IndexOutOfRangeException> oluşturmak için `throw` ifadesini kullanır.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Yöntemi çağıranlar, sonra oluşturulan özel durumu işlemek için `try-catch` veya `try-catch-finally` bloğunu kullanır. Aşağıdaki örnek, `GetNumber` yöntemiyle oluşturulan özel durumu işler.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Özel durum yeniden oluşturuluyor

`throw`, `catch` bloğunda işlenen bir özel durumu yeniden oluşturmak için bir `catch` bloğunda de kullanılabilir.  Bu durumda, `throw` bir özel durum işleneni almaz. Bir yöntem çağıran bir bağımsız değişkende diğer bir kitaplık yöntemine geçtiğinde ve kitaplık yöntemi çağırana geçirilmesi gereken bir özel durum oluşturduğunda, en çok yararlı olur. Örneğin, aşağıdaki örnek, başlatılmamış bir dizenin ilk karakterini almaya çalışırken oluşturulan <xref:System.NullReferenceException> ' ı yeniden oluşturur.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Çağırana geçirdiğiniz yeni bir özel durum oluşturmak için bir `catch` bloğunda `throw e` sözdizimini de kullanabilirsiniz. Bu durumda, <xref:System.Exception.StackTrace> özelliğinden erişilebilen özgün özel durumun yığın izlemesi korunmaz.

## <a name="the-throw-expression"></a>@No__t-0 ifadesi

7,0 ile C# başlayarak `throw`, bir deyim ve deyim olarak kullanılabilir. Bu, daha önce desteklenmeyen bağlamlarda bir özel durumun oluşturulmasına olanak sağlar. Bunlar:

- [koşullu işleç](../operators/conditional-operator.md). Aşağıdaki örnek, bir yöntem boş bir dize dizisi geçirtiyse bir <xref:System.ArgumentException> oluşturmak için bir `throw` ifadesi kullanır. 7,0 C# öncesinde, bu mantığın `if` @ no__t-2 @ no__t-3 ifadesinde görünmesi gerekir.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [null birleşim işleci](../operators/null-coalescing-operator.md). Aşağıdaki örnekte, bir `Name` özelliğine atanan dize `null` ise bir özel durum oluşturmak için bir `throw` ifadesi, null birleşim işleci ile kullanılır.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- ifade-Bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) veya yöntem. Aşağıdaki örnek, bir <xref:System.DateTime> değerine dönüştürme desteklenmediğinden <xref:System.InvalidCastException> oluşturan bir ifade-Bodied yöntemi gösterir.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [C# Anahtar Sözcükleri](index.md)
- [Nasıl yapılır: Açık özel durumlar oluşturun @ no__t-0
