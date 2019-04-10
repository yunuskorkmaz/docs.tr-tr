---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235800"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="f68bd-101">Aynı aldığı parametreleri (artı kimliği) EventSource.WriteEvent impls WriteEvent geçmelidir</span><span class="sxs-lookup"><span data-stu-id="f68bd-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f68bd-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f68bd-102">Details</span></span>|<span data-ttu-id="f68bd-103">Çalışma zamanı, artık aşağıdaki belirten sözleşmenin uygular: Öğesinden türetilen bir sınıf <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> tanımlayan bir ETW olay yöntemi temel sınıf çağırmalıdır <code>EventSource.WriteEvent</code> olay kimliği yöntemiyle ETW olay yöntemine geçilen aynı bağımsız değişkenleri tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="f68bd-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>|
|<span data-ttu-id="f68bd-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="f68bd-104">Suggestion</span></span>|<span data-ttu-id="f68bd-105">Bir <xref:System.IndexOutOfRangeException?displayProperty=name> , özel durum bir <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> okur <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> bu sözleşmeyi ihlal eden bir olay kaynağı için işlem verileri.</span><span class="sxs-lookup"><span data-stu-id="f68bd-105">An <xref:System.IndexOutOfRangeException?displayProperty=name> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data in process for an event source that violates this contract.</span></span>|
|<span data-ttu-id="f68bd-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f68bd-106">Scope</span></span>|<span data-ttu-id="f68bd-107">İkincil</span><span class="sxs-lookup"><span data-stu-id="f68bd-107">Minor</span></span>|
|<span data-ttu-id="f68bd-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f68bd-108">Version</span></span>|<span data-ttu-id="f68bd-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f68bd-109">4.5.1</span></span>|
|<span data-ttu-id="f68bd-110">Tür</span><span class="sxs-lookup"><span data-stu-id="f68bd-110">Type</span></span>|<span data-ttu-id="f68bd-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="f68bd-111">Runtime</span></span>|
