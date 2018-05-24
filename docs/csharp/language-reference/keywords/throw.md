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
---
# <a name="throw-c-reference"></a><span data-ttu-id="6f77a-102">throw (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6f77a-102">throw (C# Reference)</span></span>
<span data-ttu-id="6f77a-103">Program yürütme sırasında bir özel durum geçişi işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6f77a-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f77a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f77a-104">Remarks</span></span>

<span data-ttu-id="6f77a-105">Söz dizimi `throw` değil:</span><span class="sxs-lookup"><span data-stu-id="6f77a-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="6f77a-106">Burada `e` türetilmiş bir sınıf örneği <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f77a-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6f77a-107">Aşağıdaki örnek kullanır `throw` throw deyimini bir <xref:System.IndexOutOfRangeException> bağımsız değişkeni adlı bir yönteme aktarılırsa `GetNumber` iç dizi geçerli bir dizine karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="6f77a-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="6f77a-108">Yöntemini arayanlar sonra kullanın bir `try-catch` veya `try-catch-finally` oluşturulan özel durum işleme bloğu.</span><span class="sxs-lookup"><span data-stu-id="6f77a-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="6f77a-109">Aşağıdaki örnek tarafından oluşturulan özel durum işleme `GetNumber` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6f77a-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="6f77a-110">Bir özel durum yeniden atma</span><span class="sxs-lookup"><span data-stu-id="6f77a-110">Re-throwing an exception</span></span>

<span data-ttu-id="6f77a-111">`throw` Ayrıca, kullanılabilir bir `catch` bir özel durum yeniden throw blok işlenmiş bir `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="6f77a-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="6f77a-112">Bu durumda, `throw` bir özel durum işlenen almaz.</span><span class="sxs-lookup"><span data-stu-id="6f77a-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="6f77a-113">Bir yöntem bir bağımsız değişken bir çağrıyı yapandan diğer bazı kitaplığı yöntemine iletir ve kitaplık yöntemi, geçirilmelidir çağırana aykırı en yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6f77a-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="6f77a-114">Örneğin, aşağıdaki örnekte yeniden oluşturur bir <xref:System.NullReferenceException> başlatılmamış bir dize ilk karakteri almaya çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="6f77a-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="6f77a-115">Aynı zamanda `throw e` sözdiziminde bir `catch` çağırana geçirmesini yeni bir özel durum oluşturmak için blok.</span><span class="sxs-lookup"><span data-stu-id="6f77a-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="6f77a-116">Bu durumda, özgün özel durum yığın izlemesi olduğu kullanılabilir <xref:System.Exception.StackTrace> özelliği korunmaz.</span><span class="sxs-lookup"><span data-stu-id="6f77a-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="6f77a-117">`throw` İfade</span><span class="sxs-lookup"><span data-stu-id="6f77a-117">The `throw` expression</span></span>

<span data-ttu-id="6f77a-118">C# 7.0 ile başlayan `throw` bir deyim yanı sıra bir ifade kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f77a-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="6f77a-119">Bu, daha önce desteklenmeyen bağlamlarda durum için bir özel durum sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f77a-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="6f77a-120">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6f77a-120">These include:</span></span>

- <span data-ttu-id="6f77a-121">[koşullu işleç](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6f77a-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="6f77a-122">Aşağıdaki örnek kullanan bir `throw` throw deyimi bir <xref:System.ArgumentException> bir yöntem boş bir dize dizisi aktarılırsa.</span><span class="sxs-lookup"><span data-stu-id="6f77a-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="6f77a-123">C# 7.0 önce bu mantığı görünmesi gerekir bir `if` / `else` deyimi.</span><span class="sxs-lookup"><span data-stu-id="6f77a-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="6f77a-124">[null birleşim işlecinin](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6f77a-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="6f77a-125">Aşağıdaki örnekte, bir `throw` ifadesi null birleşim işlecinin ile dize için atanmışsa bir özel durum için kullanılan bir `Name` özelliği `null`.</span><span class="sxs-lookup"><span data-stu-id="6f77a-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- <span data-ttu-id="6f77a-126">bir ifade bodied [lambda](../../lambda-expressions.md) veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="6f77a-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="6f77a-127">Aşağıdaki örnek, oluşturur ifade bodied bir yöntemi gösterir. bir <xref:System.InvalidCastException> çünkü bir dönüştürme bir <xref:System.DateTime> değeri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6f77a-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="6f77a-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6f77a-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6f77a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f77a-129">See Also</span></span>  
 [<span data-ttu-id="6f77a-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6f77a-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6f77a-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6f77a-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6f77a-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="6f77a-132">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="6f77a-133">Try catch ve c++'ta throw deyimleri</span><span class="sxs-lookup"><span data-stu-id="6f77a-133">The try, catch, and throw Statements in C++</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="6f77a-134">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6f77a-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6f77a-135">Özel Durum İşleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="6f77a-135">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="6f77a-136">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f77a-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
