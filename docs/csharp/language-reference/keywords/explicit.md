---
title: Explicit anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: a260c6f1ccac6e09770f1cb8f43d5d872b4b2650
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610095"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="4e078-102">explicit (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4e078-102">explicit (C# Reference)</span></span>

<span data-ttu-id="4e078-103">`explicit` Anahtar sözcüğü, bir yayın ile çağrılan bir kullanıcı tanımlı tür dönüştürme işleci bildirir.</span><span class="sxs-lookup"><span data-stu-id="4e078-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span>

<span data-ttu-id="4e078-104">Aşağıdaki örnek, dönüştürür işleci tanımlar. bir `Fahrenheit` sınıfının bir `Celsius` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4e078-104">The following example defines the operator that converts from a `Fahrenheit` class to a `Celsius` class.</span></span> <span data-ttu-id="4e078-105">İşleç olmalıdır ya da iç tanımlanan bir `Fahrenheit` sınıfı veya `Celsius` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="4e078-105">The operator must be defined either inside a `Fahrenheit` class or a `Celsius` class:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="4e078-106">Aşağıdaki örnekte gösterildiği gibi bir tür dönüştürme ile tanımlı dönüştürme işleci çağırmayı:</span><span class="sxs-lookup"><span data-stu-id="4e078-106">You invoke the defined conversion operator with a cast, as the following example shows:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="4e078-107">Dönüştürme işleci bir kaynak türden hedef türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4e078-107">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="4e078-108">Kaynak türü dönüştürme işleci sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e078-108">The source type provides the conversion operator.</span></span> <span data-ttu-id="4e078-109">Örtük dönüştürme, bir atama yoluyla açık dönüştürme işleçleri çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e078-109">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="4e078-110">Bir dönüştürme işlemini özel durumlarına neden veya bilgi kaybı işaretlemelisiniz `explicit`.</span><span class="sxs-lookup"><span data-stu-id="4e078-110">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="4e078-111">Bu, derleyici sessiz bir şekilde dönüştürme işlemi muhtemelen öngörülemeyen sonuçlara yürütmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="4e078-111">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="4e078-112">Derleme zamanı hatası CS0266 atama sonuçlarında atlama.</span><span class="sxs-lookup"><span data-stu-id="4e078-112">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="4e078-113">Daha fazla bilgi için [dönüştürme işleçleri kullanarak](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4e078-113">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="4e078-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e078-114">Example</span></span>

<span data-ttu-id="4e078-115">Aşağıdaki örnek sağlayan bir `Fahrenheit` ve `Celsius` sınıfı, her biri için başka bir sınıfın açık bir dönüştürme operatörü sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e078-115">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="4e078-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e078-116">Example</span></span>

<span data-ttu-id="4e078-117">Aşağıdaki örnek, bir yapı tanımlar `Digit`, temsil eden tek bir ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="4e078-117">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="4e078-118">Bir işleç dönüştürmelerinde tanımlanan `byte` için `Digit`, ancak tüm baytlar dönüştürülebilir bir `Digit`, dönüştürme açıktır.</span><span class="sxs-lookup"><span data-stu-id="4e078-118">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="4e078-119">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4e078-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4e078-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e078-120">See also</span></span>

- [<span data-ttu-id="4e078-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4e078-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e078-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4e078-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e078-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4e078-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4e078-124">implicit</span><span class="sxs-lookup"><span data-stu-id="4e078-124">implicit</span></span>](implicit.md)
- [<span data-ttu-id="4e078-125">İşleç aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="4e078-125">Operator overloading</span></span>](../operators/operator-overloading.md)
- [<span data-ttu-id="4e078-126">Nasıl yapılır: Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama</span><span class="sxs-lookup"><span data-stu-id="4e078-126">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
- [<span data-ttu-id="4e078-127">Kullanıcı tanımlı C# ' de açık dönüştürmeler zincirleme</span><span class="sxs-lookup"><span data-stu-id="4e078-127">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
