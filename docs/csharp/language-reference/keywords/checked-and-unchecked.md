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
ms.openlocfilehash: 0ab30eb238a4db21233da612d132dfcbdb9e8895
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160521"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="a5730-103">Checked ve Unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a5730-103">Checked and Unchecked (C# Reference)</span></span>

<span data-ttu-id="a5730-104">C# deyimleri işaretli veya işaretlenmemiş bağlamda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5730-104">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="a5730-105">Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5730-105">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="a5730-106">İşaretlenmemiş bir bağlamda aritmetik taşma yok sayılır ve hedef türüne uymayan yüksek sıralı bitleri atarak sonuç kesilir.</span><span class="sxs-lookup"><span data-stu-id="a5730-106">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="a5730-107">[denetlenen](checked.md) Denetlenen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="a5730-107">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="a5730-108">[işaretlenmemiş](unchecked.md) İşaretlenmeyen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="a5730-108">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="a5730-109">Aşağıdaki işlemler taşma denetimini etkiler:</span><span class="sxs-lookup"><span data-stu-id="a5730-109">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="a5730-110">Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleçleri kullanan ifadeler:</span><span class="sxs-lookup"><span data-stu-id="a5730-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="a5730-111">`++`,, `--` birli `-` , `+` , `-` , `*` , `/`</span><span class="sxs-lookup"><span data-stu-id="a5730-111">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="a5730-112">İntegral türleri veya `float` bir integral türü arasında açık sayısal dönüştürmeler `double` .</span><span class="sxs-lookup"><span data-stu-id="a5730-112">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="a5730-113">Ne `checked` de `unchecked` belirtilmemişse, sabit olmayan ifadeler için varsayılan bağlam (çalışma zamanında değerlendirilen ifadeler) [işaretli](../compiler-options/checked-compiler-option.md) derleyici seçeneğinin değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a5730-113">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="a5730-114">Varsayılan olarak, bu seçeneğin değeri unset ve aritmetik işlemler işaretlenmemiş bir bağlamda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a5730-114">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="a5730-115">Sabit ifadeler (derleme sırasında tamamen değerlendirilebilecek ifadeler) için, varsayılan bağlam her zaman denetlenir.</span><span class="sxs-lookup"><span data-stu-id="a5730-115">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="a5730-116">Sabit bir ifade işaretsiz bir bağlam içine açıkça yerleştirilmediyse, ifadenin derleme zamanı değerlendirmesi sırasında oluşan taşmalar derleme zamanı hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a5730-116">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5730-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5730-117">See also</span></span>

- [<span data-ttu-id="a5730-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a5730-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a5730-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a5730-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a5730-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a5730-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a5730-121">Deyim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a5730-121">Statement Keywords</span></span>](statement-keywords.md)
