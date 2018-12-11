---
title: Checked ve Unchecked - C# başvurusu
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: ba4ddd7fa87eb200de0de3aea6f0bc056a40f0e5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235815"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="54e2e-102">Checked ve Unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="54e2e-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="54e2e-103">C# ifadeleri işaretli veya işaretsiz bağlam içinde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54e2e-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="54e2e-104">Denetlenen bir bağlamda aritmetik taşma bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54e2e-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="54e2e-105">İşaretlenmemiş bir bağlamda aritmetik taşma göz ardı edilir ve hedef türüne uygun olmayan herhangi bir yüksek düzeyli BITS atarak sonuç kesilmiş.</span><span class="sxs-lookup"><span data-stu-id="54e2e-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="54e2e-106">[işaretli](checked.md) içerik teslim belirtin.</span><span class="sxs-lookup"><span data-stu-id="54e2e-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="54e2e-107">[denetlenmeyen](unchecked.md) denetlenmeyen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="54e2e-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="54e2e-108">Aşağıdaki işlemleri taşma denetimi tarafından etkilenir:</span><span class="sxs-lookup"><span data-stu-id="54e2e-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="54e2e-109">Tamsayı türlerinde aşağıdaki önceden tanımlanmış işleç kullanarak ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="54e2e-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="54e2e-110">`++`, `--`, birli `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="54e2e-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="54e2e-111">Açık sayısal dönüştürmeler integral türleri arasında ya da `float` veya `double` bir integral türü.</span><span class="sxs-lookup"><span data-stu-id="54e2e-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="54e2e-112">Kullanılmazsa `checked` ya da `unchecked` belirtilirse, sabit olmayan ifade (çalışma zamanında değerlendirilir ifadeleri) için varsayılan bağlamı değeri tarafından tanımlanan [-kullanıma](../compiler-options/checked-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="54e2e-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="54e2e-113">Varsayılan olarak bu seçenek değeri ayarlanmamış ve işaretlenmemiş bir bağlamda aritmetik işlemler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="54e2e-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="54e2e-114">(Tam olarak derleme zamanında değerlendirilebilen ifadeleri) sabit ifadeler için her zaman varsayılan bağlamı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="54e2e-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="54e2e-115">Sabit bir ifade açıkça işaretlenmemiş bir bağlamda eklenmediği sürece ifadesi derleme zamanı değerlendirmesi sırasında gerçekleşen taşıyor derleme zamanı hatalarına neden.</span><span class="sxs-lookup"><span data-stu-id="54e2e-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="54e2e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54e2e-116">See Also</span></span>  

- [<span data-ttu-id="54e2e-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="54e2e-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="54e2e-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="54e2e-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="54e2e-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="54e2e-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="54e2e-120">Deyim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="54e2e-120">Statement Keywords</span></span>](statement-keywords.md)
