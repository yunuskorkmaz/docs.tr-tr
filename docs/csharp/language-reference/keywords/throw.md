---
description: throw-C# başvurusu
title: throw-C# başvurusu
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 4cad4810b89f976f92ce576917feb2398acce636
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142043"
---
# <a name="throw-c-reference"></a><span data-ttu-id="158ec-103">throw (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="158ec-103">throw (C# Reference)</span></span>

<span data-ttu-id="158ec-104">Programın yürütülmesi sırasında bir özel durumun oluşumunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="158ec-104">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="158ec-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="158ec-105">Remarks</span></span>

<span data-ttu-id="158ec-106">Sözdizimi şöyledir `throw` :</span><span class="sxs-lookup"><span data-stu-id="158ec-106">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="158ec-107">Burada `e` türetilmiş bir sınıfın örneğidir <xref:System.Exception?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="158ec-107">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="158ec-108">Aşağıdaki örnek, `throw` <xref:System.IndexOutOfRangeException> adlı bir metoda geçirilen bağımsız değişken `GetNumber` iç dizinin geçerli bir dizinine karşılık gelmiyorsa bir oluşturmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="158ec-108">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="158ec-109">Yöntem çağıranları, sonra `try-catch` `try-catch-finally` oluşturulan özel durumu işlemek için bir veya bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="158ec-109">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="158ec-110">Aşağıdaki örnek, yöntemi tarafından oluşturulan özel durumu işler `GetNumber` .</span><span class="sxs-lookup"><span data-stu-id="158ec-110">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="158ec-111">Özel durum yeniden oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="158ec-111">Re-throwing an exception</span></span>

<span data-ttu-id="158ec-112">`throw` , `catch` bir blokta işlenen bir özel durumu yeniden oluşturmak için bir blokta da kullanılabilir `catch` .</span><span class="sxs-lookup"><span data-stu-id="158ec-112">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="158ec-113">Bu durumda, `throw` bir özel durum işleneni almaz.</span><span class="sxs-lookup"><span data-stu-id="158ec-113">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="158ec-114">Bir yöntem çağıran bir bağımsız değişkende diğer bir kitaplık yöntemine geçtiğinde ve kitaplık yöntemi çağırana geçirilmesi gereken bir özel durum oluşturduğunda, en çok yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="158ec-114">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="158ec-115">Örneğin, aşağıdaki örnek, <xref:System.NullReferenceException> başlatılmamış bir dizenin ilk karakterini almaya çalışırken oluşturulan bir öğesini yeniden atar.</span><span class="sxs-lookup"><span data-stu-id="158ec-115">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="158ec-116">Ayrıca, `throw e` `catch` çağrıyı yapana geçirdiğiniz yeni bir özel durum oluşturmak için bir blokta söz dizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158ec-116">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="158ec-117">Bu durumda, özelliğinden erişilebilen özgün özel durumun yığın izlemesi <xref:System.Exception.StackTrace> korunmaz.</span><span class="sxs-lookup"><span data-stu-id="158ec-117">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="158ec-118">`throw`İfade</span><span class="sxs-lookup"><span data-stu-id="158ec-118">The `throw` expression</span></span>

<span data-ttu-id="158ec-119">C# 7,0 ' den itibaren bir deyim ve `throw` deyim olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="158ec-119">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="158ec-120">Bu, daha önce desteklenmeyen bağlamlarda bir özel durumun oluşturulmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="158ec-120">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="158ec-121">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="158ec-121">These include:</span></span>

- <span data-ttu-id="158ec-122">[koşullu işleç](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="158ec-122">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="158ec-123">Aşağıdaki örnek, bir `throw` <xref:System.ArgumentException> Yöntem boş bir dize dizisi geçirtiyse, oluşturmak için bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="158ec-123">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="158ec-124">C# 7,0 ' den önce, bu mantığın bir bildirimde görünmesi gerekir `if` / `else` .</span><span class="sxs-lookup"><span data-stu-id="158ec-124">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="158ec-125">[null birleşim işleci](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="158ec-125">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="158ec-126">Aşağıdaki örnekte bir `throw` ifade, bir özelliğe atanmış dize ise bir özel durum oluşturmak için null birleşim işleciyle birlikte kullanılır `Name` `null` .</span><span class="sxs-lookup"><span data-stu-id="158ec-126">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="158ec-127">ifade-Bodied [lambda](../operators/lambda-expressions.md) veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="158ec-127">an expression-bodied [lambda](../operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="158ec-128">Aşağıdaki örnek, bir <xref:System.InvalidCastException> değere dönüştürme desteklenmediğinden bir ifade-Bodied yöntemi gösterir <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="158ec-128">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="158ec-129">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="158ec-129">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="158ec-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="158ec-130">See also</span></span>

- [<span data-ttu-id="158ec-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="158ec-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="158ec-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="158ec-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="158ec-133">try-catch</span><span class="sxs-lookup"><span data-stu-id="158ec-133">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="158ec-134">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="158ec-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="158ec-135">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="158ec-135">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
