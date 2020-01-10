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
# <a name="throw-c-reference"></a><span data-ttu-id="bb9a9-102">throw (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bb9a9-102">throw (C# Reference)</span></span>

<span data-ttu-id="bb9a9-103">Programın yürütülmesi sırasında bir özel durumun oluşumunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb9a9-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb9a9-104">Remarks</span></span>

<span data-ttu-id="bb9a9-105">`throw` sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="bb9a9-105">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="bb9a9-106">Burada `e` <xref:System.Exception?displayProperty=nameWithType>türetilen bir sınıfın örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bb9a9-107">Aşağıdaki örnek, `GetNumber` adlı bir metoda geçirilen bağımsız değişken iç dizinin geçerli bir dizinine karşılık gelmiyorsa, bir <xref:System.IndexOutOfRangeException> oluşturmak için `throw` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="bb9a9-108">Yöntem çağıranları, sonra oluşturulan özel durumu işlemek için bir `try-catch` veya `try-catch-finally` bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="bb9a9-109">Aşağıdaki örnek, `GetNumber` metodu tarafından oluşturulan özel durumu işler.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="bb9a9-110">Özel durum yeniden oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="bb9a9-110">Re-throwing an exception</span></span>

<span data-ttu-id="bb9a9-111">`throw`, bir `catch` bloğunda işlenen bir özel durumu yeniden oluşturmak için bir `catch` bloğunda de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="bb9a9-112">Bu durumda, `throw` bir özel durum işleneni almaz.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="bb9a9-113">Bir yöntem çağıran bir bağımsız değişkende diğer bir kitaplık yöntemine geçtiğinde ve kitaplık yöntemi çağırana geçirilmesi gereken bir özel durum oluşturduğunda, en çok yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="bb9a9-114">Örneğin, aşağıdaki örnek, başlatılmamış bir dizenin ilk karakterini almaya çalışırken oluşturulan bir <xref:System.NullReferenceException> yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="bb9a9-115">Çağırana geçirdiğiniz yeni bir özel durum oluşturmak için bir `catch` bloğunda `throw e` sözdizimini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="bb9a9-116">Bu durumda, <xref:System.Exception.StackTrace> özelliğinden erişilebilen özgün özel durumun yığın izlemesi korunmaz.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="bb9a9-117">`throw` ifadesi</span><span class="sxs-lookup"><span data-stu-id="bb9a9-117">The `throw` expression</span></span>

<span data-ttu-id="bb9a9-118">7,0 ile C# başlayarak, `throw` bir deyim ve deyim olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="bb9a9-119">Bu, daha önce desteklenmeyen bağlamlarda bir özel durumun oluşturulmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="bb9a9-120">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bb9a9-120">These include:</span></span>

- <span data-ttu-id="bb9a9-121">[koşullu işleç](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bb9a9-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="bb9a9-122">Aşağıdaki örnek, bir yöntem boş bir dize dizisi geçirtiyse bir <xref:System.ArgumentException> oluşturmak için `throw` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="bb9a9-123">7,0 C# ' den önce, bu mantığın bir `if`/`else` ifadesinde görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="bb9a9-124">[null birleşim işleci](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bb9a9-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="bb9a9-125">Aşağıdaki örnekte, bir `Name` özelliğine atanan dize `null`bir özel durum oluşturmak için null birleşim işleci ile bir `throw` ifadesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="bb9a9-126">ifade-Bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="bb9a9-127">Aşağıdaki örnek, bir <xref:System.DateTime> değerine dönüştürme desteklenmediğinden bir <xref:System.InvalidCastException> oluşturan ifade-Bodied yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="bb9a9-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="bb9a9-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bb9a9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-129">See also</span></span>

- [<span data-ttu-id="bb9a9-130">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="bb9a9-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bb9a9-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb9a9-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bb9a9-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="bb9a9-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="bb9a9-133">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="bb9a9-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bb9a9-134">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb9a9-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
