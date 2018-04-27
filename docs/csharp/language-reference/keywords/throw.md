---
title: throw (C# Başvurusu)
ms.date: 03/02/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 088a8e70c5aaaae6f833f12cad1052c30fbb6bfa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="throw-c-reference"></a><span data-ttu-id="560b4-102">throw (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="560b4-102">throw (C# Reference)</span></span>
<span data-ttu-id="560b4-103">Program yürütme sırasında bir özel durum geçişi işaret eder.</span><span class="sxs-lookup"><span data-stu-id="560b4-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="560b4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="560b4-104">Remarks</span></span>

<span data-ttu-id="560b4-105">Söz dizimi `throw` değil:</span><span class="sxs-lookup"><span data-stu-id="560b4-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="560b4-106">Burada `e` türetilmiş bir sınıf örneği <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="560b4-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="560b4-107">Aşağıdaki örnek kullanır `throw` throw deyimini bir <xref:System.IndexOutOfRangeException> bağımsız değişkeni adlı bir yönteme aktarılırsa `GetNumber` iç dizi geçerli bir dizine karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="560b4-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="560b4-108">Yöntemini arayanlar sonra kullanın bir `try-catch` veya `try-catch-finally` oluşturulan özel durum işleme bloğu.</span><span class="sxs-lookup"><span data-stu-id="560b4-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="560b4-109">Aşağıdaki örnek tarafından oluşturulan özel durum işleme `GetNumber` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="560b4-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="560b4-110">Bir özel durum yeniden atma</span><span class="sxs-lookup"><span data-stu-id="560b4-110">Re-throwing an exception</span></span>

<span data-ttu-id="560b4-111">`throw` Ayrıca, kullanılabilir bir `catch` bir özel durum yeniden throw blok işlenmiş bir `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="560b4-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="560b4-112">Bu durumda, `throw` bir özel durum işlenen almaz.</span><span class="sxs-lookup"><span data-stu-id="560b4-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="560b4-113">Bir yöntem bir bağımsız değişken bir çağrıyı yapandan diğer bazı kitaplığı yöntemine iletir ve kitaplık yöntemi, geçirilmelidir çağırana aykırı en yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="560b4-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="560b4-114">Örneğin, aşağıdaki örnekte yeniden oluşturur bir <xref:System.NullReferenceException> başlatılmamış bir dize ilk karakteri almaya çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="560b4-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="560b4-115">Aynı zamanda `throw e` sözdiziminde bir `catch` çağırana geçirmesini yeni bir özel durum oluşturmak için blok.</span><span class="sxs-lookup"><span data-stu-id="560b4-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="560b4-116">Bu durumda, özgün özel durum yığın izlemesi olduğu kullanılabilir <xref:System.Exception.StackTrace> özelliği korunmaz.</span><span class="sxs-lookup"><span data-stu-id="560b4-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="560b4-117">`throw` İfade</span><span class="sxs-lookup"><span data-stu-id="560b4-117">The `throw` expression</span></span>

<span data-ttu-id="560b4-118">C# 7.0 ile başlayan `throw` bir deyim yanı sıra bir ifade kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="560b4-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="560b4-119">Bu, daha önce desteklenmeyen bağlamlarda durum için bir özel durum sağlar.</span><span class="sxs-lookup"><span data-stu-id="560b4-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="560b4-120">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="560b4-120">These include:</span></span>

- <span data-ttu-id="560b4-121">[koşullu işleç](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="560b4-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="560b4-122">Aşağıdaki örnek kullanan bir `throw` throw deyimi bir <xref:System.ArgumentException> bir yöntem boş bir dize dizisi aktarılırsa.</span><span class="sxs-lookup"><span data-stu-id="560b4-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="560b4-123">C# 7.0 önce bu mantığı görünmesi gerekir bir `if` / `else` deyimi.</span><span class="sxs-lookup"><span data-stu-id="560b4-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="560b4-124">[null birleşim işlecinin](../operators/null-conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="560b4-124">[the null-coalescing operator](../operators/null-conditional-operator.md).</span></span> <span data-ttu-id="560b4-125">Aşağıdaki örnekte, bir `throw` ifadesi null birleşim işlecinin ile dize için atanmışsa bir özel durum için kullanılan bir `Name` özelliği `null`.</span><span class="sxs-lookup"><span data-stu-id="560b4-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- <span data-ttu-id="560b4-126">bir ifade bodied [lambda](../../lambda-expressions.md) veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="560b4-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="560b4-127">Aşağıdaki örnek, oluşturur ifade bodied bir yöntemi gösterir. bir <xref:System.InvalidCastException> çünkü bir dönüştürme bir <xref:System.DateTime> değeri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="560b4-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="560b4-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="560b4-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="560b4-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="560b4-129">See Also</span></span>  
 [<span data-ttu-id="560b4-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="560b4-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="560b4-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="560b4-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="560b4-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="560b4-132">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="560b4-133">Try catch ve c++'ta throw deyimleri</span><span class="sxs-lookup"><span data-stu-id="560b4-133">The try, catch, and throw Statements in C++</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="560b4-134">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="560b4-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="560b4-135">Özel Durum İşleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="560b4-135">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="560b4-136">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="560b4-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
