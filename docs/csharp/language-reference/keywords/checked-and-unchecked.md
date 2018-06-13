---
title: Checked ve Unchecked (C# Başvurusu)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234379"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="9fa0b-102">Checked ve Unchecked (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9fa0b-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="9fa0b-103">C# ifadelerinin işaretli veya işaretsiz bağlamda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="9fa0b-104">Checked bir bağlamda aritmetik taşma bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="9fa0b-105">İşaretli bir bağlamda aritmetik taşma dikkate alınmaz ve sonucu hedef türünde uymayan tüm yüksek düzey BITS atarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="9fa0b-106">[işaretli](checked.md) işaretli belirt bağlamı.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="9fa0b-107">[Unchecked](unchecked.md) denetlenmeyen bağlamı belirtin.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="9fa0b-108">Aşağıdaki işlemleri taşma denetleyerek etkilenir:</span><span class="sxs-lookup"><span data-stu-id="9fa0b-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="9fa0b-109">Tam sayı türleri üzerinde aşağıdaki önceden tanımlanmış işleçleri kullanarak ifadeler:</span><span class="sxs-lookup"><span data-stu-id="9fa0b-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="9fa0b-110">`++`, `--`, tekli `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="9fa0b-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="9fa0b-111">Açık sayısal dönüşümler arasında tam sayı türleri, veya `float` veya `double` bir tam sayı türü.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="9fa0b-112">Ne `checked` ya da `unchecked` belirtilirse, sabit olmayan ifadeleri (çalışma zamanında değerlendirilir ifadelerde) için varsayılan bağlamı değeri tarafından tanımlanan [-işaretli](../compiler-options/checked-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="9fa0b-113">Varsayılan olarak bu seçenek unset değeri ve aritmetik işlemler işaretli bir bağlamda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="9fa0b-114">Sabit ifadeleri (derleme zamanında tam olarak değerlendirilebilir ifadelerde) için varsayılan içeriği her zaman denetlenir.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="9fa0b-115">Bir sabit ifadesine açıkça bir denetlenmeyen bağlamında eklenmediği sürece, derleme zamanı ifade değerlendirmesi sırasında ortaya taşan derleme zamanı hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9fa0b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fa0b-116">See Also</span></span>  
 [<span data-ttu-id="9fa0b-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9fa0b-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="9fa0b-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9fa0b-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="9fa0b-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9fa0b-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="9fa0b-120">Deyim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9fa0b-120">Statement Keywords</span></span>](statement-keywords.md)
