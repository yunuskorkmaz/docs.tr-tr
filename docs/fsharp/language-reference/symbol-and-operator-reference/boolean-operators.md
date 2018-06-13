---
title: Boole İşleçleri (F#)
description: 'F # programlama dili kullanılabilen Boole işleçleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563434"
---
# <a name="boolean-operators"></a><span data-ttu-id="b1dc8-103">Boole İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b1dc8-103">Boolean Operators</span></span>

<span data-ttu-id="b1dc8-104">Bu konu, F # dilinde Boole işleçleri desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="b1dc8-105">Boole işleçleri özeti</span><span class="sxs-lookup"><span data-stu-id="b1dc8-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="b1dc8-106">F # dilinde kullanılabilir Boole işleçleri aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="b1dc8-107">Bu işleçleri tarafından desteklenen tek tür `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="b1dc8-108">İşleç</span><span class="sxs-lookup"><span data-stu-id="b1dc8-108">Operator</span></span>|<span data-ttu-id="b1dc8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1dc8-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="b1dc8-110">Mantıksal olumsuzlaştırma</span><span class="sxs-lookup"><span data-stu-id="b1dc8-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="b1dc8-111">Mantıksal OR</span><span class="sxs-lookup"><span data-stu-id="b1dc8-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="b1dc8-112">Boolean ve</span><span class="sxs-lookup"><span data-stu-id="b1dc8-112">Boolean AND</span></span>|

<span data-ttu-id="b1dc8-113">Mantıksal AND ve OR işleçleri gerçekleştirmek *değerlendirmesi*, diğer bir deyişle, bunlar değerlendirmek işlecinin sağ tarafındaki ifade yalnızca ifadenin genel sonucu belirlemek gerekli olduğunda.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="b1dc8-114">İkinci bir ifade `&&` işleci yalnızca ilk ifade değerlendirilirse değerlendirildiği `true`; ikinci bir ifade `||` işleci yalnızca ilk ifade değerlendirilirse değerlendirildiği `false`.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1dc8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-115">See Also</span></span>
[<span data-ttu-id="b1dc8-116">Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="b1dc8-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="b1dc8-117">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="b1dc8-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="b1dc8-118">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b1dc8-118">Symbol and Operator Reference</span></span>](index.md)
