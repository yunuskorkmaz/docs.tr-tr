---
title: "Checked ve Unchecked (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="5d1dd-102">Checked ve Unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5d1dd-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="5d1dd-103">C# ifadelerinin işaretli veya işaretsiz bağlamda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="5d1dd-104">Checked bir bağlamda aritmetik taşma bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="5d1dd-105">İşaretli bir bağlamda aritmetik taşma göz ardı edilir ve sonuç kesilmiş.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="5d1dd-106">[işaretli](../../../csharp/language-reference/keywords/checked.md) işaretli belirt bağlamı.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="5d1dd-107">[Unchecked](../../../csharp/language-reference/keywords/unchecked.md) denetlenmeyen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="5d1dd-108">Ne `checked` ya da `unchecked` belirtilmemişse, varsayılan bağlam derleyici seçenekleri gibi dış faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="5d1dd-109">Aşağıdaki işlemleri taşma denetleyerek etkilenir:</span><span class="sxs-lookup"><span data-stu-id="5d1dd-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="5d1dd-110">Tam sayı türleri üzerinde aşağıdaki önceden tanımlanmış işleçleri kullanarak ifadeler:</span><span class="sxs-lookup"><span data-stu-id="5d1dd-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="5d1dd-111">`++``--` -(tekli) `+`  -    `*``/`</span><span class="sxs-lookup"><span data-stu-id="5d1dd-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="5d1dd-112">Açık sayısal dönüşümler tam sayı türleri arasında.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="5d1dd-113">[/ Checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) derleyici seçeneği açıkça kapsamında olmayan tüm tamsayı aritmetik ifadeler işaretli veya işaretsiz bağlamının belirtmenize olanak sağlar bir `checked` veya `unchecked` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1dd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d1dd-114">See Also</span></span>  
 [<span data-ttu-id="5d1dd-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5d1dd-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5d1dd-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5d1dd-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d1dd-117">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5d1dd-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5d1dd-118">Deyim anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5d1dd-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)
