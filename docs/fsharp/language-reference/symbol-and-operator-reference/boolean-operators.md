---
title: Boole İşleçleri (F#)
description: 'F # programlama dilinde kullanılabilen Boole işleçleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784520"
---
# <a name="boolean-operators"></a><span data-ttu-id="fd3d4-103">Boole İşleçleri</span><span class="sxs-lookup"><span data-stu-id="fd3d4-103">Boolean Operators</span></span>

<span data-ttu-id="fd3d4-104">Bu konu, F # dilinde Boole işleçleri desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fd3d4-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="fd3d4-105">Boole işleçleri özeti</span><span class="sxs-lookup"><span data-stu-id="fd3d4-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="fd3d4-106">F # dilinde kullanılabilir Boole işleçleri aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fd3d4-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="fd3d4-107">Bu işleçler tarafından desteklenen tek türüdür `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="fd3d4-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="fd3d4-108">İşleç</span><span class="sxs-lookup"><span data-stu-id="fd3d4-108">Operator</span></span>|<span data-ttu-id="fd3d4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd3d4-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="fd3d4-110">Mantıksal olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="fd3d4-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="fd3d4-111">Boole veya</span><span class="sxs-lookup"><span data-stu-id="fd3d4-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="fd3d4-112">Boole ve</span><span class="sxs-lookup"><span data-stu-id="fd3d4-112">Boolean AND</span></span>|

<span data-ttu-id="fd3d4-113">Mantıksal AND ve OR işleçlerini gerçekleştirmek *kısa devre değerlendirmesi*, diğer bir deyişle, bunlar, yalnızca genel ifadenin sonucunu belirlemek gerekli olduğunda işlecinin sağ taraftaki ifadeyi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fd3d4-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="fd3d4-114">İkinci ifadede `&&` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `true`; ikinci ifadede `||` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `false`.</span><span class="sxs-lookup"><span data-stu-id="fd3d4-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd3d4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd3d4-115">See also</span></span>

- [<span data-ttu-id="fd3d4-116">Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="fd3d4-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="fd3d4-117">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="fd3d4-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="fd3d4-118">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fd3d4-118">Symbol and Operator Reference</span></span>](index.md)
