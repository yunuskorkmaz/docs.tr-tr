---
title: Checked anahtar sözcüğü C# -başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 69bd8cc95012533a6be279b04dc883a56f6f78ea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605918"
---
# <a name="checked-c-reference"></a><span data-ttu-id="2f171-102">checked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2f171-102">checked (C# Reference)</span></span>

<span data-ttu-id="2f171-103">Anahtar `checked` sözcüğü, tam sayı türü aritmetik işlemler ve dönüştürmeler için taşma denetimini açık bir şekilde etkinleştirmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f171-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="2f171-104">Varsayılan olarak, ifade hedef türü aralığının dışında bir değer üretirse yalnızca sabit değerler içeren bir ifade bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2f171-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="2f171-105">İfade bir veya daha fazla sabit olmayan değer içeriyorsa, derleyici taşmayı algılamaz.</span><span class="sxs-lookup"><span data-stu-id="2f171-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="2f171-106">Aşağıdaki örnekte öğesine `i2` atanan ifadenin değerlendirilmesi, bir derleyici hatasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="2f171-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="2f171-107">Varsayılan olarak, bu sabit olmayan ifadeler çalışma zamanında taşma için denetlenmez ve taşma özel durumları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="2f171-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="2f171-108">Önceki örnekte iki pozitif tamsayının toplamı olarak-2.147.483.639 görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2f171-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="2f171-109">Taşma denetimi derleyici seçenekleri, ortam yapılandırması veya `checked` anahtar sözcüğünün kullanımı ile etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2f171-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="2f171-110">Aşağıdaki örneklerde, çalışma zamanında önceki Sum tarafından `checked` üretilen taşmayı `checked` algılamak için bir ifadenin veya bloğun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f171-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="2f171-111">Her iki örnek de bir taşma özel durumu yükseltir.</span><span class="sxs-lookup"><span data-stu-id="2f171-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="2f171-112">[İşaretlenmemiş](./unchecked.md) anahtar sözcük, taşma denetimini engellemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f171-112">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="2f171-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f171-113">Example</span></span>

<span data-ttu-id="2f171-114">Bu örnek, çalışma zamanında taşma `checked` denetimini etkinleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f171-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="2f171-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2f171-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2f171-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f171-116">See also</span></span>

- [<span data-ttu-id="2f171-117">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="2f171-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2f171-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2f171-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2f171-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2f171-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2f171-120">İşaretli ve İşaretsiz</span><span class="sxs-lookup"><span data-stu-id="2f171-120">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="2f171-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="2f171-121">unchecked</span></span>](./unchecked.md)
