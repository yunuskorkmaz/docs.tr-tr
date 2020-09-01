---
description: Checked anahtar sözcüğü-C# başvurusu
title: Checked anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 4dd8bc02d3af89d6bab3aef55a88cb8b40704da6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138286"
---
# <a name="checked-c-reference"></a><span data-ttu-id="4e5ba-103">checked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4e5ba-103">checked (C# Reference)</span></span>

<span data-ttu-id="4e5ba-104">`checked`Anahtar sözcüğü, tam sayı türü aritmetik işlemler ve dönüştürmeler için taşma denetimini açık bir şekilde etkinleştirmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-104">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="4e5ba-105">Varsayılan olarak, ifade hedef türü aralığının dışında bir değer üretirse yalnızca sabit değerler içeren bir ifade bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-105">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="4e5ba-106">İfade bir veya daha fazla sabit olmayan değer içeriyorsa, derleyici taşmayı algılamaz.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-106">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="4e5ba-107">Aşağıdaki örnekte öğesine atanan ifadenin değerlendirilmesi, `i2` bir derleyici hatasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-107">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="4e5ba-108">Varsayılan olarak, bu sabit olmayan ifadeler çalışma zamanında taşma için denetlenmez ve taşma özel durumları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-108">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="4e5ba-109">Önceki örnekte iki pozitif tamsayının toplamı olarak-2.147.483.639 görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-109">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="4e5ba-110">Taşma denetimi derleyici seçenekleri, ortam yapılandırması veya anahtar sözcüğünün kullanımı ile etkinleştirilebilir `checked` .</span><span class="sxs-lookup"><span data-stu-id="4e5ba-110">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="4e5ba-111">Aşağıdaki örneklerde, `checked` `checked` çalışma zamanında önceki Sum tarafından üretilen taşmayı algılamak için bir ifadenin veya bloğun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-111">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="4e5ba-112">Her iki örnek de bir taşma özel durumu yükseltir.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-112">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="4e5ba-113">[İşaretlenmemiş](./unchecked.md) anahtar sözcük, taşma denetimini engellemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-113">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="4e5ba-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e5ba-114">Example</span></span>

<span data-ttu-id="4e5ba-115">Bu örnek, `checked` çalışma zamanında taşma denetimini etkinleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-115">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="4e5ba-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4e5ba-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4e5ba-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e5ba-117">See also</span></span>

- [<span data-ttu-id="4e5ba-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4e5ba-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e5ba-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4e5ba-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e5ba-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4e5ba-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4e5ba-121">Checked ve Unchecked</span><span class="sxs-lookup"><span data-stu-id="4e5ba-121">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="4e5ba-122">unchecked</span><span class="sxs-lookup"><span data-stu-id="4e5ba-122">unchecked</span></span>](./unchecked.md)
