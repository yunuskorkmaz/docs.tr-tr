---
title: SYSLIB0004 uyarısı
description: Derleme zamanı uyarı SYSLIB0004 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: ba7cd8a890a89000b241d286c9d8069ba1398849
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333349"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="f677a-103">SYSLIB0004: kısıtlanmış yürütme bölgesi (CER) özelliği desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="f677a-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="f677a-104">[Kısıtlı yürütme bölgeleri (cer)](../../framework/performance/constrained-execution-regions.md) özelliği yalnızca .NET Framework desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f677a-104">The [Constrained execution regions (CER)](../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="f677a-105">Bu nedenle, CER ile ilgili çeşitli API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f677a-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="f677a-106">Bu API 'Lerin kullanılması, `SYSLIB0004` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f677a-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="f677a-107">Aşağıdaki CER ile ilgili API 'Ler artık kullanılmıyor:</span><span class="sxs-lookup"><span data-stu-id="f677a-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="f677a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f677a-108">See also</span></span>

- [<span data-ttu-id="f677a-109">Kısıtlı yürütme bölgeleri</span><span class="sxs-lookup"><span data-stu-id="f677a-109">Constrained execution regions</span></span>](../../framework/performance/constrained-execution-regions.md)
