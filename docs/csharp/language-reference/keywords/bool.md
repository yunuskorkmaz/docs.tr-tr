---
title: bool anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 880e8c0b733afbf5c09f543e06a5a4a858d2b456
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771855"
---
# <a name="bool-c-reference"></a><span data-ttu-id="af3d8-102">bool (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="af3d8-102">bool (C# Reference)</span></span>

<span data-ttu-id="af3d8-103">@No__t_0 anahtar sözcüğü <xref:System.Boolean?displayProperty=nameWithType> diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="af3d8-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="af3d8-104">Boole değerlerini depolamak için değişkenleri bildirmek üzere kullanılır: [true](true-literal.md) ve [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="af3d8-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="af3d8-105">Üç değerli mantığı desteklemeniz gerekiyorsa (örneğin, üç değerli bir Boole türünü destekleyen veritabanlarıyla çalışırken) `bool?` türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="af3d8-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="af3d8-106">@No__t_0 işlenenleri için, önceden tanımlanmış `&` ve `|` işleçleri üç değerli mantığı destekler.</span><span class="sxs-lookup"><span data-stu-id="af3d8-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="af3d8-107">Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="af3d8-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="af3d8-108">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="af3d8-108">Literals</span></span>

<span data-ttu-id="af3d8-109">Bir `bool` değişkenine Boole değeri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af3d8-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="af3d8-110">Ayrıca, bir `bool` değişkenine `bool` değerlendirilen bir ifade da atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af3d8-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="af3d8-111">Bir `bool` değişkeninin varsayılan değeri `false`.</span><span class="sxs-lookup"><span data-stu-id="af3d8-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="af3d8-112">Bir `bool?` değişkeninin varsayılan değeri `null`.</span><span class="sxs-lookup"><span data-stu-id="af3d8-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="af3d8-113">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="af3d8-113">Conversions</span></span>

<span data-ttu-id="af3d8-114">' C++De, `bool` türünde bir değer `int` türünde bir değere dönüştürülebilir. diğer bir deyişle, `false` sıfır ile eşdeğerdir ve `true` sıfır dışında bir değere eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="af3d8-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="af3d8-115">' C#De, `bool` türü ve diğer türler arasında dönüştürme yok.</span><span class="sxs-lookup"><span data-stu-id="af3d8-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="af3d8-116">Örneğin, aşağıdaki `if` ifade içinde C#geçersizdir:</span><span class="sxs-lookup"><span data-stu-id="af3d8-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="af3d8-117">@No__t_0 türünde bir değişkeni test etmek için, bunu aşağıdaki gibi, sıfır gibi bir değerle açıkça karşılaştırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="af3d8-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="af3d8-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="af3d8-118">Example</span></span>

<span data-ttu-id="af3d8-119">Bu örnekte, klavyeden bir karakter girersiniz ve program giriş karakterinin bir harf olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="af3d8-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="af3d8-120">Bir harf ise, küçük harf veya büyük harf olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="af3d8-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="af3d8-121">Bu denetimler, her ikisi de `bool` türünü döndüren <xref:System.Char.IsLetter%2A> ve <xref:System.Char.IsLower%2A> ile gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="af3d8-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="af3d8-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="af3d8-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="af3d8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af3d8-123">See also</span></span>

- [<span data-ttu-id="af3d8-124">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="af3d8-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="af3d8-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="af3d8-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="af3d8-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="af3d8-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="af3d8-127">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="af3d8-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="af3d8-128">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="af3d8-128">Built-In Types Table</span></span>](./built-in-types-table.md)
