---
title: bool (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 1045a459491b0d0d6a84c60f6e820297b47efd5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215978"
---
# <a name="bool-c-reference"></a><span data-ttu-id="09574-102">bool (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="09574-102">bool (C# Reference)</span></span>
<span data-ttu-id="09574-103">`bool` Sözcüktür bir diğer ad <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09574-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="09574-104">Boole değerlerini depolamak için değişkenleri bildirmek için kullanılan [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="09574-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09574-105">Ayrıca değeri olabilir bir Boolean değişkeni gerektirip gerektirmediğini `null`, kullanmak `bool?`.</span><span class="sxs-lookup"><span data-stu-id="09574-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="09574-106">Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="09574-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="09574-107">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="09574-107">Literals</span></span>  
 <span data-ttu-id="09574-108">Bir Boolean değeri atayabilirsiniz bir `bool` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="09574-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="09574-109">Ayrıca değerlendiren bir ifade atayabilirsiniz `bool` için bir `bool` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="09574-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 <span data-ttu-id="09574-110">Varsayılan değer olan bir `bool` değişken `false`.</span><span class="sxs-lookup"><span data-stu-id="09574-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="09574-111">Varsayılan değer olan bir `bool?` değişken `null`.</span><span class="sxs-lookup"><span data-stu-id="09574-111">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="09574-112">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="09574-112">Conversions</span></span>  
 <span data-ttu-id="09574-113">C++, türünde bir değer `bool` türünde bir değer dönüştürülebilir `int`; diğer bir deyişle, `false` sıfır olarak eşdeğerdir ve `true` için sıfır olmayan değerler eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="09574-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="09574-114">C# ' ta yok arasında dönüştürme `bool` türü ve diğer türleri.</span><span class="sxs-lookup"><span data-stu-id="09574-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="09574-115">Örneğin, aşağıdaki `if` deyimi C# ' geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="09574-115">For example, the following `if` statement is invalid in C#:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 <span data-ttu-id="09574-116">Türünde bir değişken test etmek için `int`, açıkça sıfır gibi bir değer gibi karşılaştırın gerekir:</span><span class="sxs-lookup"><span data-stu-id="09574-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="09574-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="09574-117">Example</span></span>  
 <span data-ttu-id="09574-118">Bu örnekte, klavyeden bir karakter girin ve program giriş karakteri bir harf olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="09574-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="09574-119">Bir harf ise küçük harfler veya büyük olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="09574-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="09574-120">Bu denetimler ile gerçekleştirilen <xref:System.Char.IsLetter%2A>, ve <xref:System.Char.IsLower%2A>, hangi return her ikisi de `bool` türü:</span><span class="sxs-lookup"><span data-stu-id="09574-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="09574-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="09574-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09574-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09574-122">See Also</span></span>  
 [<span data-ttu-id="09574-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="09574-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="09574-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="09574-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="09574-125">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="09574-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="09574-126">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="09574-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="09574-127">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="09574-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="09574-128">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="09574-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="09574-129">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="09574-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
