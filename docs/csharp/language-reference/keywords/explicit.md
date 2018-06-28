---
title: Explicit anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 66d271fdac0bad356ee0bafc1732e2f410854da1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027947"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="5784d-102">explicit (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5784d-102">explicit (C# Reference)</span></span>

<span data-ttu-id="5784d-103">`explicit` Anahtar sözcüğü ile bir cast çağrılan bir kullanıcı tanımlı tür dönüştürme işleci bildirir.</span><span class="sxs-lookup"><span data-stu-id="5784d-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="5784d-104">Örneğin, bu işleç Fahrenhayt derece adlı bir sınıf olarak adlandırılan bir sınıftan dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="5784d-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="5784d-105">Bu dönüşüm işleci çağrılan şöyle:</span><span class="sxs-lookup"><span data-stu-id="5784d-105">This conversion operator can be invoked like this:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="5784d-106">Dönüşüm işleci kaynak türünden bir hedef türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5784d-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="5784d-107">Kaynak türü dönüşüm işleci sağlar.</span><span class="sxs-lookup"><span data-stu-id="5784d-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="5784d-108">Örtük dönüştürme, açık dönüşüm işleçleri atama yoluyla çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5784d-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="5784d-109">Dönüştürme işlemi özel durumlara neden bilgileri kaybeder veya işaretlemeniz gerekir `explicit`.</span><span class="sxs-lookup"><span data-stu-id="5784d-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="5784d-110">Bu, büyük olasılıkla öngörülemeyen sonuçlara dönüştürme işlemi sessizce çağırma derleyici önler.</span><span class="sxs-lookup"><span data-stu-id="5784d-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="5784d-111">Derleme zamanı hatası CS0266 cast sonuçlarında atlama.</span><span class="sxs-lookup"><span data-stu-id="5784d-111">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="5784d-112">Daha fazla bilgi için bkz: [dönüşüm işleçleri kullanma](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5784d-112">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="5784d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="5784d-113">Example</span></span>

<span data-ttu-id="5784d-114">Aşağıdaki örnek sağlayan bir `Fahrenheit` ve `Celsius` sınıfı, her biri bir açık dönüşüm işleci için başka bir sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="5784d-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="5784d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5784d-115">Example</span></span>

<span data-ttu-id="5784d-116">Aşağıdaki örnek, bir yapının tanımlar `Digit`, tek bir ondalık basamak temsil eden.</span><span class="sxs-lookup"><span data-stu-id="5784d-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="5784d-117">Bir işleç dönüştürmeleri için tanımlanan `byte` için `Digit`, ancak tüm bayt dönüştürülebilir bir `Digit`, dönüştürme açık değildir.</span><span class="sxs-lookup"><span data-stu-id="5784d-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="5784d-118">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5784d-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5784d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5784d-119">See also</span></span>

[<span data-ttu-id="5784d-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5784d-120">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="5784d-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5784d-121">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="5784d-122">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5784d-122">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="5784d-123">implicit</span><span class="sxs-lookup"><span data-stu-id="5784d-123">implicit</span></span>](implicit.md)  
[<span data-ttu-id="5784d-124">işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5784d-124">operator (C# Reference)</span></span>](operator.md)  
[<span data-ttu-id="5784d-125">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="5784d-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
[<span data-ttu-id="5784d-126">Kullanıcı tanımlı zincirleme açık dönüşümler C#</span><span class="sxs-lookup"><span data-stu-id="5784d-126">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  