---
title: Boole İşleçleri (F#)
description: 'F # programlama dili kullanılabilen Boole işleçleri hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0b11b5133b02b6f507c7886b2fbaebf30abf46cb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="boolean-operators"></a><span data-ttu-id="911fe-103">Boole İşleçleri</span><span class="sxs-lookup"><span data-stu-id="911fe-103">Boolean Operators</span></span>

<span data-ttu-id="911fe-104">Bu konu, F # dilinde Boole işleçleri desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="911fe-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="911fe-105">Boole işleçleri özeti</span><span class="sxs-lookup"><span data-stu-id="911fe-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="911fe-106">F # dilinde kullanılabilir Boole işleçleri aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="911fe-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="911fe-107">Bu işleçleri tarafından desteklenen tek tür `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="911fe-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="911fe-108">İşleç</span><span class="sxs-lookup"><span data-stu-id="911fe-108">Operator</span></span>|<span data-ttu-id="911fe-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="911fe-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="911fe-110">Mantıksal olumsuzlaştırma</span><span class="sxs-lookup"><span data-stu-id="911fe-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="911fe-111">Mantıksal OR</span><span class="sxs-lookup"><span data-stu-id="911fe-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="911fe-112">Boolean ve</span><span class="sxs-lookup"><span data-stu-id="911fe-112">Boolean AND</span></span>|

<span data-ttu-id="911fe-113">Mantıksal AND ve OR işleçleri gerçekleştirmek *değerlendirmesi*, diğer bir deyişle, bunlar değerlendirmek işlecinin sağ tarafındaki ifade yalnızca ifadenin genel sonucu belirlemek gerekli olduğunda.</span><span class="sxs-lookup"><span data-stu-id="911fe-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="911fe-114">İkinci bir ifade `&&` işleci yalnızca ilk ifade değerlendirilirse değerlendirildiği `true`; ikinci bir ifade `||` işleci yalnızca ilk ifade değerlendirilirse değerlendirildiği `false`.</span><span class="sxs-lookup"><span data-stu-id="911fe-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="911fe-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="911fe-115">See Also</span></span>
[<span data-ttu-id="911fe-116">Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="911fe-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="911fe-117">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="911fe-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="911fe-118">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="911fe-118">Symbol and Operator Reference</span></span>](index.md)
