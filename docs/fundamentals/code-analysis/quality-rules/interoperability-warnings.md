---
title: Taşınabilirlik ve birlikte çalışabilirlik kuralları (kod analizi)
description: Kod Analizi kuralı taşınabilirlik ve birlikte çalışabilirlik kuralları hakkında bilgi edinin
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96588821"
---
# <a name="portability-and-interoperability-rules"></a><span data-ttu-id="3add1-103">Taşınabilirlik ve birlikte çalışabilirlik kuralları</span><span class="sxs-lookup"><span data-stu-id="3add1-103">Portability and interoperability rules</span></span>

<span data-ttu-id="3add1-104">Taşınabilirlik kuralları farklı platformlarda taşınabilirliği destekler.</span><span class="sxs-lookup"><span data-stu-id="3add1-104">Portability rules support portability across different platforms.</span></span> <span data-ttu-id="3add1-105">Birlikte çalışabilirlik kuralları COM istemcileriyle etkileşimi destekler.</span><span class="sxs-lookup"><span data-stu-id="3add1-105">Interoperability rules support interaction with COM clients.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3add1-106">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="3add1-106">In this section</span></span>

| <span data-ttu-id="3add1-107">Kural</span><span class="sxs-lookup"><span data-stu-id="3add1-107">Rule</span></span> | <span data-ttu-id="3add1-108">Description</span><span class="sxs-lookup"><span data-stu-id="3add1-108">Description</span></span> |
| - | - |
| [<span data-ttu-id="3add1-109">CA1401: P/Invoke görünür olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="3add1-109">CA1401: P/Invokes should not be visible</span></span>](ca1401.md) | <span data-ttu-id="3add1-110">Ortak bir türdeki ortak veya korumalı yöntemin System.Runtime.InteropServices.DllImportAttribute özniteliği vardır (Ayrıca, Visual Basic Declare anahtar sözcüğü tarafından uygulanır).</span><span class="sxs-lookup"><span data-stu-id="3add1-110">A public or protected method in a public type has the System.Runtime.InteropServices.DllImportAttribute attribute (also implemented by the Declare keyword in Visual Basic).</span></span> <span data-ttu-id="3add1-111">Bu tür yöntemler açıkta kalmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3add1-111">Such methods should not be exposed.</span></span> |
| [<span data-ttu-id="3add1-112">CA1416: Platform uyumluluğunu doğrula</span><span class="sxs-lookup"><span data-stu-id="3add1-112">CA1416: Validate platform compatibility</span></span>](ca1416.md) | <span data-ttu-id="3add1-113">Bir bileşende platforma bağımlı API 'Lerin kullanılması, kodun artık tüm platformlarda çalışmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3add1-113">Using platform-dependent APIs on a component makes the code no longer work across all platforms.</span></span> |
| [<span data-ttu-id="3add1-114">CA1417: `OutAttribute` P/Invoke için dize parametrelerinde kullanmayın</span><span class="sxs-lookup"><span data-stu-id="3add1-114">CA1417: Do not use `OutAttribute` on string parameters for P/Invokes</span></span>](ca1417.md) | <span data-ttu-id="3add1-115">Değeri ile geçirilen dize parametreleri, `OutAttribute` dize birbirine bağlı bir dizeyse çalışma zamanının kararlılığını bozabilir.</span><span class="sxs-lookup"><span data-stu-id="3add1-115">String parameters passed by value with the `OutAttribute` can destabilize the runtime if the string is an interned string.</span></span> |
