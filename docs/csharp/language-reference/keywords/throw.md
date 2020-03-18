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
# <a name="throw-c-reference"></a><span data-ttu-id="5cbd8-102">throw (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5cbd8-102">throw (C# Reference)</span></span>

<span data-ttu-id="5cbd8-103">Program yürütülmesi sırasında bir özel durum oluşumunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cbd8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cbd8-104">Remarks</span></span>

<span data-ttu-id="5cbd8-105">`throw` Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="5cbd8-105">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="5cbd8-106">nereden `e` türetilmiş bir sınıfın <xref:System.Exception?displayProperty=nameWithType>bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5cbd8-107">Aşağıdaki örnek, `throw` adlı `GetNumber` bir <xref:System.IndexOutOfRangeException> yönteme geçirilen bağımsız değişken iç dizinin geçerli bir dizine karşılık gelmiyorsa, bir ifade yi atmak için deyimkullanır.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="5cbd8-108">Yöntem arayanlar daha `try-catch` sonra `try-catch-finally` atılan özel durumu işlemek için bir veya blok kullanır.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="5cbd8-109">Aşağıdaki örnek, `GetNumber` yöntem tarafından atılan özel durumu işler.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="5cbd8-110">Bir özel durumu yeniden atma</span><span class="sxs-lookup"><span data-stu-id="5cbd8-110">Re-throwing an exception</span></span>

<span data-ttu-id="5cbd8-111">`throw`bir `catch` blokta işlenen `catch` bir özel durum yeniden atmak için bir blokta da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="5cbd8-112">Bu durumda, `throw` bir istisna operand almaz.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="5cbd8-113">Bir yöntem, bir arayandan başka bir kitaplık yöntemine bir bağımsız değişken geçtiğinde ve kitaplık yöntemi arayana aktarılması gereken bir özel durum attığında en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="5cbd8-114">Örneğin, aşağıdaki örnek, başharfe <xref:System.NullReferenceException> çevrilmemiş bir dizenin ilk karakterini almaya çalışırken atılan bir şeyi yeniden atar.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="5cbd8-115">Arayanın aktardığı `throw e` yeni bir `catch` özel durumu anında anımsamak için bir bloktaki sözdizimini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="5cbd8-116">Bu durumda, <xref:System.Exception.StackTrace> özellikten kullanılabilen özgün özel durumun yığın izi korunmaz.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="5cbd8-117">İfade `throw`</span><span class="sxs-lookup"><span data-stu-id="5cbd8-117">The `throw` expression</span></span>

<span data-ttu-id="5cbd8-118">C# 7.0 ile `throw` başlayarak, bir ifade yanı sıra bir ifade olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="5cbd8-119">Bu, daha önce desteklenmeyen bağlamlarda bir özel durum atılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="5cbd8-120">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="5cbd8-120">These include:</span></span>

- <span data-ttu-id="5cbd8-121">[koşullu işleç](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5cbd8-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="5cbd8-122">Aşağıdaki örnekte, `throw` boş bir <xref:System.ArgumentException> dize dizisi geçirilirse bir yöntem atmak için bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="5cbd8-123">C# 7.0'dan önce, bu mantığın bir `if` / `else` deyimde görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="5cbd8-124">[null-coalescing operatörü](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5cbd8-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="5cbd8-125">Aşağıdaki örnekte, `throw` bir `Name` özel liğe atanan dize `null`.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="5cbd8-126">bir ifade gövdeli [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) veya yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="5cbd8-127">Aşağıdaki örnekte, bir <xref:System.InvalidCastException> <xref:System.DateTime> değere dönüşüm desteklenmez bir çünkü atan bir ifade gövdeli yöntem gösterin.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="5cbd8-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5cbd8-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5cbd8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cbd8-129">See also</span></span>

- [<span data-ttu-id="5cbd8-130">C# Referans</span><span class="sxs-lookup"><span data-stu-id="5cbd8-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5cbd8-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5cbd8-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5cbd8-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="5cbd8-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="5cbd8-133">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="5cbd8-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5cbd8-134">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5cbd8-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
