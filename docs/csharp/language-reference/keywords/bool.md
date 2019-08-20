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
ms.openlocfilehash: 3e4e83b52cd6b275e68039693c774f6490f2b88f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606051"
---
# <a name="bool-c-reference"></a><span data-ttu-id="6d717-102">bool (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6d717-102">bool (C# Reference)</span></span>

<span data-ttu-id="6d717-103">Anahtar sözcüğü öğesinin <xref:System.Boolean?displayProperty=nameWithType>diğer adıdır. `bool`</span><span class="sxs-lookup"><span data-stu-id="6d717-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d717-104">Boole değerlerini depolamak için değişkenleri bildirmek üzere kullanılır: [true](true-literal.md) ve [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="6d717-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6d717-105">Üç değerli mantığı desteklemeniz gerekiyorsa, örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken türünükullanın.`bool?`</span><span class="sxs-lookup"><span data-stu-id="6d717-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="6d717-106">İşlenenler için, önceden tanımlanmış `&` ve `|` işleçleri üç değerli mantığı destekler. `bool?`</span><span class="sxs-lookup"><span data-stu-id="6d717-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="6d717-107">Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6d717-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="6d717-108">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="6d717-108">Literals</span></span>

<span data-ttu-id="6d717-109">Bir `bool` değişkene Boole değeri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d717-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="6d717-110">Ayrıca, bir `bool` `bool` değişkenine değerlendirilen bir ifade atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d717-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="6d717-111">`bool` Bir`false`değişkenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="6d717-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="6d717-112">`bool?` Bir`null`değişkenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="6d717-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="6d717-113">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="6d717-113">Conversions</span></span>

<span data-ttu-id="6d717-114">' C++De, türünde `bool` bir değer türünde `int`bir değere dönüştürülebilir; diğer bir deyişle, `false` sıfıra eşdeğerdir ve `true` sıfır dışında değerlere eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6d717-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="6d717-115">İçinde C#, `bool` türü ve diğer türler arasında dönüştürme yoktur.</span><span class="sxs-lookup"><span data-stu-id="6d717-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="6d717-116">Örneğin, aşağıdaki `if` ifade içinde C#geçersizdir:</span><span class="sxs-lookup"><span data-stu-id="6d717-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="6d717-117">Türün `int`bir değişkenini test etmek için, bunu aşağıdaki gibi sıfır gibi bir değerle açıkça karşılaştırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6d717-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="6d717-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d717-118">Example</span></span>

<span data-ttu-id="6d717-119">Bu örnekte, klavyeden bir karakter girersiniz ve program giriş karakterinin bir harf olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="6d717-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="6d717-120">Bir harf ise, küçük harf veya büyük harf olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="6d717-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="6d717-121">Bu denetimler, <xref:System.Char.IsLetter%2A> herikisi<xref:System.Char.IsLower%2A>de türüdöndürenveilegerçekleştirilir:`bool`</span><span class="sxs-lookup"><span data-stu-id="6d717-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="6d717-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6d717-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6d717-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d717-123">See also</span></span>

- [<span data-ttu-id="6d717-124">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="6d717-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6d717-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6d717-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6d717-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6d717-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="6d717-127">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="6d717-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="6d717-128">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="6d717-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="6d717-129">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="6d717-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="6d717-130">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="6d717-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
