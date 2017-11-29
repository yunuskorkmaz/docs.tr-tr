---
title: "Boole İşleçleri (F#)"
description: "F # programlama dili kullanılabilen Boole işleçleri hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a><span data-ttu-id="4e48e-104">Boole İşleçleri</span><span class="sxs-lookup"><span data-stu-id="4e48e-104">Boolean Operators</span></span>

<span data-ttu-id="4e48e-105">Bu konu, F # dilinde Boole işleçleri desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e48e-105">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="4e48e-106">Boole işleçleri özeti</span><span class="sxs-lookup"><span data-stu-id="4e48e-106">Summary of Boolean Operators</span></span>
<span data-ttu-id="4e48e-107">F # dilinde kullanılabilir Boole işleçleri aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e48e-107">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="4e48e-108">Bu işleçleri tarafından desteklenen tek tür `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="4e48e-108">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="4e48e-109">İşleç</span><span class="sxs-lookup"><span data-stu-id="4e48e-109">Operator</span></span>|<span data-ttu-id="4e48e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e48e-110">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="4e48e-111">Mantıksal olumsuzlaştırma</span><span class="sxs-lookup"><span data-stu-id="4e48e-111">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="4e48e-112">Mantıksal OR</span><span class="sxs-lookup"><span data-stu-id="4e48e-112">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="4e48e-113">Boolean ve</span><span class="sxs-lookup"><span data-stu-id="4e48e-113">Boolean AND</span></span>|

<span data-ttu-id="4e48e-114">Mantıksal AND ve OR işleçleri gerçekleştirmek *değerlendirmesi*, diğer bir deyişle, bunlar değerlendirmek işlecinin sağ tarafındaki ifade yalnızca ifadenin genel sonucu belirlemek gerekli olduğunda.</span><span class="sxs-lookup"><span data-stu-id="4e48e-114">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="4e48e-115">İkinci bir ifade `&&` işleci yalnızca ilk ifade değerlendirilirse değerlendirildiği `true`; ikinci bir ifade `||` işleci yalnızca ilk ifade değerlendirilirse değerlendirildiği `false`.</span><span class="sxs-lookup"><span data-stu-id="4e48e-115">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e48e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e48e-116">See Also</span></span>
[<span data-ttu-id="4e48e-117">Bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="4e48e-117">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="4e48e-118">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="4e48e-118">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="4e48e-119">Simge ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="4e48e-119">Symbol and Operator Reference</span></span>](index.md)
