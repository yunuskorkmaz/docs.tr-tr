---
title: Boole İşleçleri
description: Kullanılabilen Boole işleçleri hakkında bilgi edinin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612744"
---
# <a name="boolean-operators"></a><span data-ttu-id="75026-103">Boole İşleçleri</span><span class="sxs-lookup"><span data-stu-id="75026-103">Boolean Operators</span></span>

<span data-ttu-id="75026-104">Bu konuda Boole işleçleri için destek açıklanır F# dili.</span><span class="sxs-lookup"><span data-stu-id="75026-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="75026-105">Boole işleçleri özeti</span><span class="sxs-lookup"><span data-stu-id="75026-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="75026-106">Kullanılabilen Boole işleçleri aşağıdaki tabloda özetlenmiştir F# dili.</span><span class="sxs-lookup"><span data-stu-id="75026-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="75026-107">Bu işleçler tarafından desteklenen tek türüdür `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="75026-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="75026-108">İşleç</span><span class="sxs-lookup"><span data-stu-id="75026-108">Operator</span></span>|<span data-ttu-id="75026-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75026-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="75026-110">Mantıksal olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="75026-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="75026-111">Boole veya</span><span class="sxs-lookup"><span data-stu-id="75026-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="75026-112">Boole ve</span><span class="sxs-lookup"><span data-stu-id="75026-112">Boolean AND</span></span>|

<span data-ttu-id="75026-113">Mantıksal AND ve OR işleçlerini gerçekleştirmek *kısa devre değerlendirmesi*, diğer bir deyişle, bunlar, yalnızca genel ifadenin sonucunu belirlemek gerekli olduğunda işlecinin sağ taraftaki ifadeyi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="75026-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="75026-114">İkinci ifadede `&&` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `true`; ikinci ifadede `||` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `false`.</span><span class="sxs-lookup"><span data-stu-id="75026-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="75026-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75026-115">See also</span></span>

- [<span data-ttu-id="75026-116">Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="75026-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="75026-117">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="75026-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="75026-118">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="75026-118">Symbol and Operator Reference</span></span>](index.md)