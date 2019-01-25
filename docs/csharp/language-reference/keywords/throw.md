---
title: throw - C# başvurusu
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
ms.openlocfilehash: 4e29c0cc85f0ec6ccd3f428d64121f53b91ae9a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713856"
---
# <a name="throw-c-reference"></a><span data-ttu-id="1852f-102">throw (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1852f-102">throw (C# Reference)</span></span>

<span data-ttu-id="1852f-103">Programın yürütülmesi sırasında bir özel durum oluşumunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1852f-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1852f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1852f-104">Remarks</span></span>

<span data-ttu-id="1852f-105">Söz dizimi `throw` olan:</span><span class="sxs-lookup"><span data-stu-id="1852f-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```

<span data-ttu-id="1852f-106">Burada `e` türetilmiş bir sınıfın bir örneği <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1852f-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1852f-107">Aşağıdaki örnekte `throw` throw deyimini bir <xref:System.IndexOutOfRangeException> adlı bir yönteme geçirilen bağımsız değişken varsa `GetNumber` iç dizi geçerli bir dizine karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="1852f-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="1852f-108">Ardından yöntemi çağıranlar kullanmak bir `try-catch` veya `try-catch-finally` oluşan özel durum işleme bloğu.</span><span class="sxs-lookup"><span data-stu-id="1852f-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="1852f-109">Aşağıdaki örnek tarafından oluşturulan özel durum işleme `GetNumber` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1852f-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="1852f-110">Bir özel durum yeniden oluşturma</span><span class="sxs-lookup"><span data-stu-id="1852f-110">Re-throwing an exception</span></span>

<span data-ttu-id="1852f-111">`throw` Ayrıca, kullanılabilir bir `catch` işlenen bir özel durumu yeniden harekete geçirileceğini blok içinde bir `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="1852f-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="1852f-112">Bu durumda, `throw` bir özel durum işleneni almaz.</span><span class="sxs-lookup"><span data-stu-id="1852f-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="1852f-113">Bir yöntem bağımsız değişken üzerinde bir çağrıyı yapandan için başka bir kitaplık yöntemi geçirir ve kitaplık yöntemini çağırana geçirilmelidir bir özel durum oluşturur ekseriyetle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="1852f-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="1852f-114">Örneğin, aşağıdaki örnekte hatayı yeniden harekete bir <xref:System.NullReferenceException> başlatılmamış bir dizenin ilk karakteri alınmaya çalışılırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="1852f-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="1852f-115">Ayrıca `throw e` sözdiziminde bir `catch` çağırana geçirmesini yeni bir özel durum oluşturmak için blok.</span><span class="sxs-lookup"><span data-stu-id="1852f-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="1852f-116">Bu durumda, özgün özel durumun yığın izlemesi, kullanılabilir <xref:System.Exception.StackTrace> özelliği korunmaz.</span><span class="sxs-lookup"><span data-stu-id="1852f-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="1852f-117">`throw` İfadesi</span><span class="sxs-lookup"><span data-stu-id="1852f-117">The `throw` expression</span></span>

<span data-ttu-id="1852f-118">C# 7.0 ile başlayan `throw` bir deyim yanı sıra bir deyim kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1852f-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="1852f-119">Bu, daha önce desteklenmeyen bağlamlarda oluşturulması bir özel durum verir.</span><span class="sxs-lookup"><span data-stu-id="1852f-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="1852f-120">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1852f-120">These include:</span></span>

- <span data-ttu-id="1852f-121">[koşullu işleç](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1852f-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="1852f-122">Aşağıdaki örnekte bir `throw` throw deyimi bir <xref:System.ArgumentException> , bir yöntem boş bir dize dizisi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1852f-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="1852f-123">C# 7.0 önce bu mantık görünmesi gerekir bir `if` / `else` deyimi.</span><span class="sxs-lookup"><span data-stu-id="1852f-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="1852f-124">[null birleşim işleci](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1852f-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="1852f-125">Aşağıdaki örnekte, bir `throw` ifade null birleşim işleci ile dize için atanan bir özel durum için kullanılan bir `Name` özelliği `null`.</span><span class="sxs-lookup"><span data-stu-id="1852f-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- <span data-ttu-id="1852f-126">ifade gövdeli [lambda](../../lambda-expressions.md) veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="1852f-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="1852f-127">Oluşturan bir ifade gövdeli yöntem aşağıdaki örnekte bir <xref:System.InvalidCastException> çünkü dönüştürme bir <xref:System.DateTime> değeri desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="1852f-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="1852f-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1852f-128">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1852f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1852f-129">See also</span></span>

- [<span data-ttu-id="1852f-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1852f-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1852f-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1852f-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1852f-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="1852f-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="1852f-133">Try, catch ve throw deyimleri c++</span><span class="sxs-lookup"><span data-stu-id="1852f-133">The try, catch, and throw Statements in C++</span></span>](try-catch.md)
- [<span data-ttu-id="1852f-134">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1852f-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1852f-135">Özel Durum İşleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="1852f-135">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="1852f-136">Nasıl yapılır: Açıkça özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="1852f-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
