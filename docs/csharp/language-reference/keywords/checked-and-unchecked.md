---
title: İşaretli ve İşaretsiz - C# Başvurusu
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 8ee4c481a30dce30029fbe8cc26f4798b523a7ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173646"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="07c6f-102">Checked ve Unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="07c6f-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="07c6f-103">C# deyimleri denetlenen veya denetlenmemiş bağlamında yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="07c6f-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="07c6f-104">Denetlenen bir bağlamda, aritmetik taşma bir özel durum yükseltir.</span><span class="sxs-lookup"><span data-stu-id="07c6f-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="07c6f-105">Denetlenmemiş bir bağlamda, aritmetik taşması yoksayılır ve sonuç hedef türüne uymayan yüksek sıralı bitler atılarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="07c6f-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="07c6f-106">[kontrol edildi](checked.md) Denetlenen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="07c6f-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="07c6f-107">[işaretlenmemiş](unchecked.md) İşaretlenmemiş bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="07c6f-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="07c6f-108">Aşağıdaki işlemler taşma denetiminden etkilenir:</span><span class="sxs-lookup"><span data-stu-id="07c6f-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="07c6f-109">İntegral türlerinde aşağıdaki önceden tanımlanmış işleçleri kullanan ifadeler:</span><span class="sxs-lookup"><span data-stu-id="07c6f-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="07c6f-110">`++`, `--`, `-`unary `-` `*`, `+`, ,`/`</span><span class="sxs-lookup"><span data-stu-id="07c6f-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="07c6f-111">İntegral türleri arasında veya integral `float` `double` türünden veya integral türünden açık sayısal dönüşümler.</span><span class="sxs-lookup"><span data-stu-id="07c6f-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="07c6f-112">Ne `checked` belirtilmişse ne de `unchecked` belirtilmişse, sabit olmayan ifadeler (çalışma zamanında değerlendirilen ifadeler) için varsayılan [bağlam, -denetlenen](../compiler-options/checked-compiler-option.md) derleyici seçeneğinin değeriyle tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07c6f-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="07c6f-113">Varsayılan olarak, bu seçeneğin değeri ayarlanmamış ve aritmetik işlemler denetlenmemiş bir bağlamda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="07c6f-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="07c6f-114">Sabit ifadeler (derleme zamanında tam olarak değerlendirilebilen ifadeler) için varsayılan bağlam her zaman denetlenir.</span><span class="sxs-lookup"><span data-stu-id="07c6f-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="07c6f-115">Sabit bir ifade açıkça denetlenmemiş bir içeriğe yerleştirilmediği sürece, ifadenin derleme zamanı değerlendirmesi sırasında oluşan taşmalar derleme zamanı hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="07c6f-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="07c6f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07c6f-116">See also</span></span>

- [<span data-ttu-id="07c6f-117">C# Referans</span><span class="sxs-lookup"><span data-stu-id="07c6f-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07c6f-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="07c6f-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="07c6f-119">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="07c6f-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="07c6f-120">Deyim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="07c6f-120">Statement Keywords</span></span>](statement-keywords.md)
