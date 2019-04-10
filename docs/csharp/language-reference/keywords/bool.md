---
title: bool anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d87da29872582e9c0d47a6c999312ce88252a5cc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334178"
---
# <a name="bool-c-reference"></a><span data-ttu-id="b7c35-102">bool (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b7c35-102">bool (C# Reference)</span></span>

<span data-ttu-id="b7c35-103">`bool` Anahtar sözcüğü, bir diğer adını <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7c35-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b7c35-104">Boole değerleri depolamak üzere değişkenler bildirmek için kullanılır: [true](true-literal.md) ve [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b7c35-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b7c35-105">Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli Boole türü destekleyen veritabanları ile.</span><span class="sxs-lookup"><span data-stu-id="b7c35-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="b7c35-106">İçin `bool?` işlenenler, önceden tanımlanmış `&` ve `|` üç değerli mantıksal işleçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b7c35-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="b7c35-107">Daha fazla bilgi için [boş değer atanabilir Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümünü [Boolean mantıksal işleçler](../operators/boolean-logical-operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="b7c35-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="b7c35-108">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="b7c35-108">Literals</span></span>

<span data-ttu-id="b7c35-109">Bir Boolean değerine atayabilirsiniz bir `bool` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b7c35-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="b7c35-110">İçin değerlendirilen bir ifade de atayabilirsiniz `bool` için bir `bool` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b7c35-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="b7c35-111">Varsayılan değer olan bir `bool` değişkendir `false`.</span><span class="sxs-lookup"><span data-stu-id="b7c35-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="b7c35-112">Varsayılan değer olan bir `bool?` değişkendir `null`.</span><span class="sxs-lookup"><span data-stu-id="b7c35-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="b7c35-113">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="b7c35-113">Conversions</span></span>

<span data-ttu-id="b7c35-114">C++ ' türünde bir değer `bool` türün değerine dönüştürülebilir `int`; diğer bir deyişle, `false` Sıfıra eşdeğer olan ve `true` sıfır olmayan değerlere eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b7c35-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="b7c35-115">C# ' ta yoktur arasında dönüştürme `bool` türü ve diğer türleri.</span><span class="sxs-lookup"><span data-stu-id="b7c35-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="b7c35-116">Örneğin, aşağıdaki `if` ifadesi C# içinde geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="b7c35-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="b7c35-117">Türünde bir değişken test etmek için `int`, açıkça gibi sıfır, bir değer gibi karşılaştırın gerekir:</span><span class="sxs-lookup"><span data-stu-id="b7c35-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="b7c35-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7c35-118">Example</span></span>

<span data-ttu-id="b7c35-119">Bu örnekte, bir karakter klavyeden girmeniz ve program, girdi karakteri bir harf olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="b7c35-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="b7c35-120">Bir harf ise, küçük harfler veya büyük olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="b7c35-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="b7c35-121">Bu denetimler ile gerçekleştirilen <xref:System.Char.IsLetter%2A>, ve <xref:System.Char.IsLower%2A>, hangi iade her ikisi de `bool` türü:</span><span class="sxs-lookup"><span data-stu-id="b7c35-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="b7c35-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b7c35-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b7c35-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7c35-123">See also</span></span>

- [<span data-ttu-id="b7c35-124">C# Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b7c35-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="b7c35-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b7c35-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b7c35-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b7c35-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="b7c35-127">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="b7c35-127">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="b7c35-128">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="b7c35-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="b7c35-129">Örtük Sayısal Dönüşümler Tablosu</span><span class="sxs-lookup"><span data-stu-id="b7c35-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="b7c35-130">Açık Sayısal Dönüşümler Tablosu</span><span class="sxs-lookup"><span data-stu-id="b7c35-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
