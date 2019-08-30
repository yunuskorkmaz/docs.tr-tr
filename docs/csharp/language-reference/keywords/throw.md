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
# <a name="throw-c-reference"></a><span data-ttu-id="122d8-102">throw (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="122d8-102">throw (C# Reference)</span></span>

<span data-ttu-id="122d8-103">Programın yürütülmesi sırasında bir özel durumun oluşumunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="122d8-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="122d8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="122d8-104">Remarks</span></span>

<span data-ttu-id="122d8-105">Sözdizimi `throw` şöyledir:</span><span class="sxs-lookup"><span data-stu-id="122d8-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```

<span data-ttu-id="122d8-106">`e` burada<xref:System.Exception?displayProperty=nameWithType>türetilmiş bir sınıfın örneğidir.</span><span class="sxs-lookup"><span data-stu-id="122d8-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="122d8-107">Aşağıdaki örnek, adlı `throw` `GetNumber` bir metoda geçirilen bağımsız değişken <xref:System.IndexOutOfRangeException> iç dizinin geçerli bir dizinine karşılık gelmiyorsa bir oluşturmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="122d8-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="122d8-108">Yöntem çağıranları, sonra `try-catch` oluşturulan `try-catch-finally` özel durumu işlemek için bir veya bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="122d8-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="122d8-109">Aşağıdaki örnek, `GetNumber` yöntemi tarafından oluşturulan özel durumu işler.</span><span class="sxs-lookup"><span data-stu-id="122d8-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="122d8-110">Özel durum yeniden oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="122d8-110">Re-throwing an exception</span></span>

<span data-ttu-id="122d8-111">`throw`, bir `catch` `catch` blokta işlenen bir özel durumu yeniden oluşturmak için bir blokta da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="122d8-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="122d8-112">Bu durumda, `throw` bir özel durum işleneni almaz.</span><span class="sxs-lookup"><span data-stu-id="122d8-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="122d8-113">Bir yöntem çağıran bir bağımsız değişkende diğer bir kitaplık yöntemine geçtiğinde ve kitaplık yöntemi çağırana geçirilmesi gereken bir özel durum oluşturduğunda, en çok yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="122d8-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="122d8-114">Örneğin, aşağıdaki örnek, başlatılmamış bir dizenin ilk karakterini <xref:System.NullReferenceException> almaya çalışırken oluşturulan bir öğesini yeniden atar.</span><span class="sxs-lookup"><span data-stu-id="122d8-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="122d8-115">Ayrıca, çağrıyı yapana geçirdiğiniz `throw e` yeni bir özel `catch` durum oluşturmak için bir blokta söz dizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="122d8-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="122d8-116">Bu durumda, <xref:System.Exception.StackTrace> özelliğinden erişilebilen özgün özel durumun yığın izlemesi korunmaz.</span><span class="sxs-lookup"><span data-stu-id="122d8-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="122d8-117">`throw` İfade</span><span class="sxs-lookup"><span data-stu-id="122d8-117">The `throw` expression</span></span>

<span data-ttu-id="122d8-118">7,0 ile C# başlayarak, `throw` bir deyim ve deyim olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="122d8-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="122d8-119">Bu, daha önce desteklenmeyen bağlamlarda bir özel durumun oluşturulmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="122d8-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="122d8-120">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="122d8-120">These include:</span></span>

- <span data-ttu-id="122d8-121">[koşullu işleç](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="122d8-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="122d8-122">Aşağıdaki örnek, bir yöntem `throw` boş bir dize dizisi <xref:System.ArgumentException> geçirtiyse, oluşturmak için bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="122d8-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="122d8-123">7,0 C# öncesinde, bu mantığın bir `if` / `else` bildirimde görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="122d8-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="122d8-124">[null birleşim işleci](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="122d8-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="122d8-125">Aşağıdaki örnekte `throw` bir ifade, bir `Name` özelliğe atanmış dize ise `null`bir özel durum oluşturmak için null birleşim işleciyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="122d8-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- <span data-ttu-id="122d8-126">ifade-Bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="122d8-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="122d8-127">Aşağıdaki örnek, bir <xref:System.InvalidCastException> <xref:System.DateTime> değere dönüştürme desteklenmediğinden bir ifade-Bodied yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="122d8-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="122d8-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="122d8-128">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="122d8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="122d8-129">See also</span></span>

- [<span data-ttu-id="122d8-130">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="122d8-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="122d8-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="122d8-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="122d8-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="122d8-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="122d8-133">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="122d8-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="122d8-134">Nasıl yapılır: Özel durumları açık olarak oluştur</span><span class="sxs-lookup"><span data-stu-id="122d8-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
