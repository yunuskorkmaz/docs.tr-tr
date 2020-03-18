---
title: kontrol edilen anahtar kelime - C# Referans
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713703"
---
# <a name="checked-c-reference"></a><span data-ttu-id="e52c2-102">checked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e52c2-102">checked (C# Reference)</span></span>

<span data-ttu-id="e52c2-103">Anahtar `checked` kelime, integral türü aritmetik işlemleri ve dönüşümleri için taşma denetimini açıkça etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e52c2-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="e52c2-104">Varsayılan olarak, yalnızca sabit değerler içeren bir ifade, ifade hedef türünün aralığıdışında bir değer üretirse derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e52c2-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="e52c2-105">İfade bir veya daha fazla sabit olmayan değerler içeriyorsa, derleyici taşma algılamaz.</span><span class="sxs-lookup"><span data-stu-id="e52c2-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="e52c2-106">Aşağıdaki `i2` örnekte atanan ifadeyi değerlendirmek derleyici hatasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="e52c2-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="e52c2-107">Varsayılan olarak, bu sabit olmayan ifadeler de çalışma zamanında taşma için denetlenmez ve taşma özel durumları yükseltmez.</span><span class="sxs-lookup"><span data-stu-id="e52c2-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="e52c2-108">Önceki örnekte -2,147,483,639 iki pozitif tamsaın toplamı olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e52c2-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="e52c2-109">Taşma denetimi derleyici seçenekleri, ortam yapılandırması `checked` veya anahtar kelimenin kullanımı yla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e52c2-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="e52c2-110">Aşağıdaki örnekler, önceki toplamın çalışma zamanında ürettiği taşmayı algılamak için bir `checked` ifadenin veya bloğun `checked` nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e52c2-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="e52c2-111">Her iki örnek de bir taşma özel durum yükseltmek.</span><span class="sxs-lookup"><span data-stu-id="e52c2-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="e52c2-112">[Denetlenemeyen](./unchecked.md) anahtar kelime taşma denetimini önlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e52c2-112">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="e52c2-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e52c2-113">Example</span></span>

<span data-ttu-id="e52c2-114">Bu örnek, çalışma `checked` zamanında taşma denetimini etkinleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e52c2-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="e52c2-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e52c2-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e52c2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e52c2-116">See also</span></span>

- [<span data-ttu-id="e52c2-117">C# Referans</span><span class="sxs-lookup"><span data-stu-id="e52c2-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e52c2-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e52c2-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e52c2-119">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="e52c2-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="e52c2-120">Checked ve Unchecked</span><span class="sxs-lookup"><span data-stu-id="e52c2-120">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="e52c2-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="e52c2-121">unchecked</span></span>](./unchecked.md)
