---
description: Checked ve unchecked-C# başvurusu
title: Checked ve unchecked-C# başvurusu
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a8d6a26e28062da682689bf64a9e38ea5fd158b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138273"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="fc445-103">Checked ve Unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fc445-103">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="fc445-104">C# deyimleri işaretli veya işaretlenmemiş bağlamda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc445-104">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="fc445-105">Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc445-105">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="fc445-106">İşaretlenmemiş bir bağlamda aritmetik taşma yok sayılır ve hedef türüne uymayan yüksek sıralı bitleri atarak sonuç kesilir.</span><span class="sxs-lookup"><span data-stu-id="fc445-106">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="fc445-107">[denetlenen](checked.md) Denetlenen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="fc445-107">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="fc445-108">[işaretlenmemiş](unchecked.md) İşaretlenmeyen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="fc445-108">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="fc445-109">Aşağıdaki işlemler taşma denetimini etkiler:</span><span class="sxs-lookup"><span data-stu-id="fc445-109">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="fc445-110">Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleçleri kullanan ifadeler:</span><span class="sxs-lookup"><span data-stu-id="fc445-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="fc445-111">`++`,, `--` birli `-` , `+` , `-` , `*` , `/`</span><span class="sxs-lookup"><span data-stu-id="fc445-111">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="fc445-112">İntegral türleri veya `float` bir integral türü arasında açık sayısal dönüştürmeler `double` .</span><span class="sxs-lookup"><span data-stu-id="fc445-112">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="fc445-113">Ne `checked` de `unchecked` belirtilmemişse, sabit olmayan ifadeler için varsayılan bağlam (çalışma zamanında değerlendirilen ifadeler) [işaretli](../compiler-options/checked-compiler-option.md) derleyici seçeneğinin değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fc445-113">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="fc445-114">Varsayılan olarak, bu seçeneğin değeri unset ve aritmetik işlemler işaretlenmemiş bir bağlamda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="fc445-114">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="fc445-115">Sabit ifadeler (derleme sırasında tamamen değerlendirilebilecek ifadeler) için, varsayılan bağlam her zaman denetlenir.</span><span class="sxs-lookup"><span data-stu-id="fc445-115">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="fc445-116">Sabit bir ifade işaretsiz bir bağlam içine açıkça yerleştirilmediyse, ifadenin derleme zamanı değerlendirmesi sırasında oluşan taşmalar derleme zamanı hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fc445-116">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fc445-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc445-117">See also</span></span>

- [<span data-ttu-id="fc445-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fc445-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc445-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fc445-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc445-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fc445-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fc445-121">Deyim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fc445-121">Statement Keywords</span></span>](statement-keywords.md)
