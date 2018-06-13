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
ms.openlocfilehash: c7e944f224ff9bf6dc3b8cefc293182bb79f74f2
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457514"
---
# <a name="throw-c-reference"></a>throw (C# Başvurusu)
Program yürütme sırasında bir özel durum geçişi işaret eder.  
  
## <a name="remarks"></a>Açıklamalar

Söz dizimi `throw` değil:

```csharp
throw [e]
```
Burada `e` türetilmiş bir sınıf örneği <xref:System.Exception?displayProperty=nameWithType>. Aşağıdaki örnek kullanır `throw` throw deyimini bir <xref:System.IndexOutOfRangeException> bağımsız değişkeni adlı bir yönteme aktarılırsa `GetNumber` iç dizi geçerli bir dizine karşılık gelmiyor.

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Yöntemini arayanlar sonra kullanın bir `try-catch` veya `try-catch-finally` oluşturulan özel durum işleme bloğu. Aşağıdaki örnek tarafından oluşturulan özel durum işleme `GetNumber` yöntemi.

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Bir özel durum yeniden atma

`throw` Ayrıca, kullanılabilir bir `catch` bir özel durum yeniden throw blok işlenmiş bir `catch` bloğu.  Bu durumda, `throw` bir özel durum işlenen almaz. Bir yöntem bir bağımsız değişken bir çağrıyı yapandan diğer bazı kitaplığı yöntemine iletir ve kitaplık yöntemi, geçirilmelidir çağırana aykırı en yararlı olacaktır. Örneğin, aşağıdaki örnekte yeniden oluşturur bir <xref:System.NullReferenceException> başlatılmamış bir dize ilk karakteri almaya çalışırken oluşur. 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Aynı zamanda `throw e` sözdiziminde bir `catch` çağırana geçirmesini yeni bir özel durum oluşturmak için blok. Bu durumda, özgün özel durum yığın izlemesi olduğu kullanılabilir <xref:System.Exception.StackTrace> özelliği korunmaz.
 
## <a name="the-throw-expression"></a>`throw` İfade

C# 7.0 ile başlayan `throw` bir deyim yanı sıra bir ifade kullanılabilir. Bu, daha önce desteklenmeyen bağlamlarda durum için bir özel durum sağlar. Bu güncelleştirmeler şunlardır:

- [koşullu işleç](../operators/conditional-operator.md). Aşağıdaki örnek kullanan bir `throw` throw deyimi bir <xref:System.ArgumentException> bir yöntem boş bir dize dizisi aktarılırsa. C# 7.0 önce bu mantığı görünmesi gerekir bir `if` / `else` deyimi.

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [null birleşim işlecinin](../operators/null-coalescing-operator.md). Aşağıdaki örnekte, bir `throw` ifadesi null birleşim işlecinin ile dize için atanmışsa bir özel durum için kullanılan bir `Name` özelliği `null`.
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- bir ifade bodied [lambda](../../lambda-expressions.md) veya yöntem. Aşağıdaki örnek, oluşturur ifade bodied bir yöntemi gösterir. bir <xref:System.InvalidCastException> çünkü bir dönüştürme bir <xref:System.DateTime> değeri desteklenmez.
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [Try catch ve c++'ta throw deyimleri](../../../csharp/language-reference/keywords/try-catch.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Özel Durum İşleme Deyimleri](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
