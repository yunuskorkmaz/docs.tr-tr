---
title: İşaretli ve Işaretsiz C# başvuru
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a3b1ef8e6d8e496eda74ab25b3fe17f8174bac11
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713713"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="98f51-102">Checked ve Unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="98f51-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="98f51-103">C#deyimler işaretli veya işaretlenmemiş bağlamda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="98f51-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="98f51-104">Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98f51-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="98f51-105">İşaretlenmemiş bir bağlamda aritmetik taşma yok sayılır ve hedef türüne uymayan yüksek sıralı bitleri atarak sonuç kesilir.</span><span class="sxs-lookup"><span data-stu-id="98f51-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="98f51-106">[denetlenen](checked.md) Denetlenen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="98f51-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="98f51-107">[işaretlenmemiş](unchecked.md) İşaretlenmeyen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="98f51-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="98f51-108">Aşağıdaki işlemler taşma denetimini etkiler:</span><span class="sxs-lookup"><span data-stu-id="98f51-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="98f51-109">Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleçleri kullanan ifadeler:</span><span class="sxs-lookup"><span data-stu-id="98f51-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="98f51-110">`++`, `--`, birli `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="98f51-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="98f51-111">İntegral türleri arasında veya `float` ya da `double` bir integral türüne açık sayısal dönüştürmeler.</span><span class="sxs-lookup"><span data-stu-id="98f51-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="98f51-112">Ne `checked` ne de `unchecked` belirtilmemişse, sabit olmayan ifadeler (çalışma zamanında değerlendirilen ifadeler) için varsayılan bağlam, [-Checked](../compiler-options/checked-compiler-option.md) derleyici seçeneğinin değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="98f51-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="98f51-113">Varsayılan olarak, bu seçeneğin değeri unset ve aritmetik işlemler işaretlenmemiş bir bağlamda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="98f51-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="98f51-114">Sabit ifadeler (derleme sırasında tamamen değerlendirilebilecek ifadeler) için, varsayılan bağlam her zaman denetlenir.</span><span class="sxs-lookup"><span data-stu-id="98f51-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="98f51-115">Sabit bir ifade işaretsiz bir bağlam içine açıkça yerleştirilmediyse, ifadenin derleme zamanı değerlendirmesi sırasında oluşan taşmalar derleme zamanı hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="98f51-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98f51-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98f51-116">See also</span></span>

- [<span data-ttu-id="98f51-117">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="98f51-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="98f51-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98f51-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98f51-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="98f51-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="98f51-120">Deyim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="98f51-120">Statement Keywords</span></span>](statement-keywords.md)
