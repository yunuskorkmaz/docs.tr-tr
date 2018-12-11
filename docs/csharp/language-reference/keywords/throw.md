---
title: throw (C# Başvurusu)
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
ms.openlocfilehash: 2f9bf1a012740978f66784ea8986ef940c66e74f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126402"
---
# <a name="throw-c-reference"></a>throw (C# Başvurusu)

Programın yürütülmesi sırasında bir özel durum oluşumunu bildirir.  
  
## <a name="remarks"></a>Açıklamalar

Söz dizimi `throw` olan:

```csharp
throw [e]
```

Burada `e` türetilmiş bir sınıfın bir örneği <xref:System.Exception?displayProperty=nameWithType>. Aşağıdaki örnekte `throw` throw deyimini bir <xref:System.IndexOutOfRangeException> adlı bir yönteme geçirilen bağımsız değişken varsa `GetNumber` iç dizi geçerli bir dizine karşılık gelmiyor.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Ardından yöntemi çağıranlar kullanmak bir `try-catch` veya `try-catch-finally` oluşan özel durum işleme bloğu. Aşağıdaki örnek tarafından oluşturulan özel durum işleme `GetNumber` yöntemi.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Bir özel durum yeniden oluşturma

`throw` Ayrıca, kullanılabilir bir `catch` işlenen bir özel durumu yeniden harekete geçirileceğini blok içinde bir `catch` blok.  Bu durumda, `throw` bir özel durum işleneni almaz. Bir yöntem bağımsız değişken üzerinde bir çağrıyı yapandan için başka bir kitaplık yöntemi geçirir ve kitaplık yöntemini çağırana geçirilmelidir bir özel durum oluşturur ekseriyetle faydalıdır. Örneğin, aşağıdaki örnekte hatayı yeniden harekete bir <xref:System.NullReferenceException> başlatılmamış bir dizenin ilk karakteri alınmaya çalışılırken oluşur.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Ayrıca `throw e` sözdiziminde bir `catch` çağırana geçirmesini yeni bir özel durum oluşturmak için blok. Bu durumda, özgün özel durumun yığın izlemesi, kullanılabilir <xref:System.Exception.StackTrace> özelliği korunmaz.

## <a name="the-throw-expression"></a>`throw` İfadesi

C# 7.0 ile başlayan `throw` bir deyim yanı sıra bir deyim kullanılabilir. Bu, daha önce desteklenmeyen bağlamlarda oluşturulması bir özel durum verir. Bu güncelleştirmeler şunlardır:

- [koşullu işleç](../operators/conditional-operator.md). Aşağıdaki örnekte bir `throw` throw deyimi bir <xref:System.ArgumentException> , bir yöntem boş bir dize dizisi olarak geçirilir. C# 7.0 önce bu mantık görünmesi gerekir bir `if` / `else` deyimi.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [null birleşim işleci](../operators/null-coalescing-operator.md). Aşağıdaki örnekte, bir `throw` ifade null birleşim işleci ile dize için atanan bir özel durum için kullanılan bir `Name` özelliği `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- ifade gövdeli [lambda](../../lambda-expressions.md) veya yöntem. Oluşturan bir ifade gövdeli yöntem aşağıdaki örnekte bir <xref:System.InvalidCastException> çünkü dönüştürme bir <xref:System.DateTime> değeri desteklenmiyor.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a>C# dili belirtimi  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [try-catch](try-catch.md)  
- [Try, catch ve throw deyimleri c++](try-catch.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [Özel Durum İşleme Deyimleri](exception-handling-statements.md)  
- [Nasıl Yapılır: Açıkça özel durumlar oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)