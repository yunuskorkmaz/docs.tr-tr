---
description: unchecked anahtar sözcüğü-C# başvurusu
title: unchecked anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: bb66639e3657b247b9ebcad1594daf1f57a5c76b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141991"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="a4c02-103">unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a4c02-103">unchecked (C# Reference)</span></span>

<span data-ttu-id="a4c02-104">`unchecked`Anahtar sözcüğü, tamsayı türü aritmetik işlemler ve dönüştürmeler için taşma denetlemeyi gizlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4c02-104">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="a4c02-105">İşaretlenmemiş bir bağlamda, bir ifade hedef türü aralığının dışında bir değer üretirse, taşma işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="a4c02-105">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="a4c02-106">Örneğin, aşağıdaki örnekteki hesaplama bir `unchecked` blok veya ifadede gerçekleştirildiğinden, sonucun bir tamsayı için çok büyük olması ve `int1` -2.147.483.639 değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="a4c02-106">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="a4c02-107">`unchecked`Ortam kaldırılırsa, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="a4c02-107">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="a4c02-108">İfadenin tüm terimleri sabitler olduğundan, derleme sırasında taşma tespit edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c02-108">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="a4c02-109">Sabit olmayan terimleri içeren ifadeler, derleme zamanında ve çalışma zamanında varsayılan olarak işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="a4c02-109">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="a4c02-110">Denetlenen bir ortamı etkinleştirme hakkında bilgi için bkz. [denetlenir](checked.md) .</span><span class="sxs-lookup"><span data-stu-id="a4c02-110">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="a4c02-111">Taşma için denetim zaman alacağından, hiçbir tehlike olmaması durumunda Denetlenmemiş kod kullanımı performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c02-111">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="a4c02-112">Ancak, taşma olasılığa karşı, denetlenen bir ortam kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c02-112">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="a4c02-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4c02-113">Example</span></span>

<span data-ttu-id="a4c02-114">Bu örnek, anahtar sözcüğünün nasıl kullanılacağını gösterir `unchecked` .</span><span class="sxs-lookup"><span data-stu-id="a4c02-114">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="a4c02-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a4c02-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a4c02-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4c02-116">See also</span></span>

- [<span data-ttu-id="a4c02-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a4c02-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a4c02-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a4c02-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a4c02-119">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a4c02-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a4c02-120">Checked ve Unchecked</span><span class="sxs-lookup"><span data-stu-id="a4c02-120">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="a4c02-121">edildikten</span><span class="sxs-lookup"><span data-stu-id="a4c02-121">checked</span></span>](checked.md)
