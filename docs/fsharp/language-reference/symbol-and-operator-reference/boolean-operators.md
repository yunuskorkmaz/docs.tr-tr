---
title: Boole İşleçleri (F#)
description: F# programlama dilinde kullanılabilen Boole işleçleri hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45638486"
---
# <a name="boolean-operators"></a><span data-ttu-id="b2a18-103">Boole İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b2a18-103">Boolean Operators</span></span>

<span data-ttu-id="b2a18-104">Bu konu, F# dilinde Boole işleçleri desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b2a18-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="b2a18-105">Boole işleçleri özeti</span><span class="sxs-lookup"><span data-stu-id="b2a18-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="b2a18-106">F# dilinde kullanılabilir Boole işleçleri aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b2a18-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="b2a18-107">Bu işleçler tarafından desteklenen tek türüdür `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="b2a18-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="b2a18-108">İşleç</span><span class="sxs-lookup"><span data-stu-id="b2a18-108">Operator</span></span>|<span data-ttu-id="b2a18-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2a18-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="b2a18-110">Mantıksal olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="b2a18-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="b2a18-111">Boole veya</span><span class="sxs-lookup"><span data-stu-id="b2a18-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="b2a18-112">Boole ve</span><span class="sxs-lookup"><span data-stu-id="b2a18-112">Boolean AND</span></span>|

<span data-ttu-id="b2a18-113">Mantıksal AND ve OR işleçlerini gerçekleştirmek *kısa devre değerlendirmesi*, diğer bir deyişle, bunlar, yalnızca genel ifadenin sonucunu belirlemek gerekli olduğunda işlecinin sağ taraftaki ifadeyi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b2a18-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="b2a18-114">İkinci ifadede `&&` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `true`; ikinci ifadede `||` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `false`.</span><span class="sxs-lookup"><span data-stu-id="b2a18-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2a18-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2a18-115">See also</span></span>

- [<span data-ttu-id="b2a18-116">Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="b2a18-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="b2a18-117">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="b2a18-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="b2a18-118">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b2a18-118">Symbol and Operator Reference</span></span>](index.md)
