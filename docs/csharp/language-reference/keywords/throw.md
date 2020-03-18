---
title: atmak - C# Referans
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399338"
---
# <a name="throw-c-reference"></a>throw (C# Başvurusu)

Program yürütülmesi sırasında bir özel durum oluşumunu bildirir.  
  
## <a name="remarks"></a>Açıklamalar

`throw` Sözdizimi:

```csharp
throw [e];
```

nereden `e` türetilmiş bir sınıfın <xref:System.Exception?displayProperty=nameWithType>bir örneğidir. Aşağıdaki örnek, `throw` adlı `GetNumber` bir <xref:System.IndexOutOfRangeException> yönteme geçirilen bağımsız değişken iç dizinin geçerli bir dizine karşılık gelmiyorsa, bir ifade yi atmak için deyimkullanır.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Yöntem arayanlar daha `try-catch` sonra `try-catch-finally` atılan özel durumu işlemek için bir veya blok kullanır. Aşağıdaki örnek, `GetNumber` yöntem tarafından atılan özel durumu işler.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Bir özel durumu yeniden atma

`throw`bir `catch` blokta işlenen `catch` bir özel durum yeniden atmak için bir blokta da kullanılabilir.  Bu durumda, `throw` bir istisna operand almaz. Bir yöntem, bir arayandan başka bir kitaplık yöntemine bir bağımsız değişken geçtiğinde ve kitaplık yöntemi arayana aktarılması gereken bir özel durum attığında en kullanışlıdır. Örneğin, aşağıdaki örnek, başharfe <xref:System.NullReferenceException> çevrilmemiş bir dizenin ilk karakterini almaya çalışırken atılan bir şeyi yeniden atar.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Arayanın aktardığı `throw e` yeni bir `catch` özel durumu anında anımsamak için bir bloktaki sözdizimini de kullanabilirsiniz. Bu durumda, <xref:System.Exception.StackTrace> özellikten kullanılabilen özgün özel durumun yığın izi korunmaz.

## <a name="the-throw-expression"></a>İfade `throw`

C# 7.0 ile `throw` başlayarak, bir ifade yanı sıra bir ifade olarak kullanılabilir. Bu, daha önce desteklenmeyen bağlamlarda bir özel durum atılmasına izin verir. Bunlar:

- [koşullu işleç](../operators/conditional-operator.md). Aşağıdaki örnekte, `throw` boş bir <xref:System.ArgumentException> dize dizisi geçirilirse bir yöntem atmak için bir ifade kullanır. C# 7.0'dan önce, bu mantığın bir `if` / `else` deyimde görünmesi gerekir.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [null-coalescing operatörü](../operators/null-coalescing-operator.md). Aşağıdaki örnekte, `throw` bir `Name` özel liğe atanan dize `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- bir ifade gövdeli [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) veya yöntemi. Aşağıdaki örnekte, bir <xref:System.InvalidCastException> <xref:System.DateTime> değere dönüşüm desteklenmez bir çünkü atan bir ifade gövdeli yöntem gösterin.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [C# Anahtar Kelimeler](index.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
