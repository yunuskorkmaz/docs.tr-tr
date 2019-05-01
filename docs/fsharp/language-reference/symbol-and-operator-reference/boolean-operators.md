---
title: Boole İşleçleri
description: Kullanılabilen Boole işleçleri hakkında bilgi edinin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925820"
---
# <a name="boolean-operators"></a><span data-ttu-id="8aba0-103">Boole İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8aba0-103">Boolean Operators</span></span>

<span data-ttu-id="8aba0-104">Bu konuda Boole işleçleri için destek açıklanır F# dili.</span><span class="sxs-lookup"><span data-stu-id="8aba0-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="8aba0-105">Boole işleçleri özeti</span><span class="sxs-lookup"><span data-stu-id="8aba0-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="8aba0-106">Kullanılabilen Boole işleçleri aşağıdaki tabloda özetlenmiştir F# dili.</span><span class="sxs-lookup"><span data-stu-id="8aba0-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="8aba0-107">Bu işleçler tarafından desteklenen tek türüdür `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="8aba0-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="8aba0-108">İşleç</span><span class="sxs-lookup"><span data-stu-id="8aba0-108">Operator</span></span>|<span data-ttu-id="8aba0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aba0-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="8aba0-110">Mantıksal olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="8aba0-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="8aba0-111">Boole veya</span><span class="sxs-lookup"><span data-stu-id="8aba0-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="8aba0-112">Boole ve</span><span class="sxs-lookup"><span data-stu-id="8aba0-112">Boolean AND</span></span>|

<span data-ttu-id="8aba0-113">Mantıksal AND ve OR işleçlerini gerçekleştirmek *kısa devre değerlendirmesi*, diğer bir deyişle, bunlar, yalnızca genel ifadenin sonucunu belirlemek gerekli olduğunda işlecinin sağ taraftaki ifadeyi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8aba0-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="8aba0-114">İkinci ifadede `&&` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `true`; ikinci ifadede `||` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `false`.</span><span class="sxs-lookup"><span data-stu-id="8aba0-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8aba0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8aba0-115">See also</span></span>

- [<span data-ttu-id="8aba0-116">Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="8aba0-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="8aba0-117">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="8aba0-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="8aba0-118">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8aba0-118">Symbol and Operator Reference</span></span>](index.md)