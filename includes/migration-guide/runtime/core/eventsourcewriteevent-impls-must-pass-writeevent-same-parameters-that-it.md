---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61842056"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="8f784-101">Aynı aldığı parametreleri (artı kimliği) EventSource.WriteEvent impls WriteEvent geçmelidir</span><span class="sxs-lookup"><span data-stu-id="8f784-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8f784-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8f784-102">Details</span></span>|<span data-ttu-id="8f784-103">Çalışma zamanı, artık aşağıdaki belirten sözleşmenin uygular: Öğesinden türetilen bir sınıf <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> tanımlayan bir ETW olay yöntemi temel sınıf çağırmalıdır <code>EventSource.WriteEvent</code> olay kimliği yöntemiyle ETW olay yöntemine geçilen aynı bağımsız değişkenleri tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="8f784-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>|
|<span data-ttu-id="8f784-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="8f784-104">Suggestion</span></span>|<span data-ttu-id="8f784-105">Bir <xref:System.IndexOutOfRangeException?displayProperty=name> , özel durum bir <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> okur <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> bu sözleşmeyi ihlal eden bir olay kaynağı için işlem verileri.</span><span class="sxs-lookup"><span data-stu-id="8f784-105">An <xref:System.IndexOutOfRangeException?displayProperty=name> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data in process for an event source that violates this contract.</span></span>|
|<span data-ttu-id="8f784-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8f784-106">Scope</span></span>|<span data-ttu-id="8f784-107">İkincil</span><span class="sxs-lookup"><span data-stu-id="8f784-107">Minor</span></span>|
|<span data-ttu-id="8f784-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8f784-108">Version</span></span>|<span data-ttu-id="8f784-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8f784-109">4.5.1</span></span>|
|<span data-ttu-id="8f784-110">Tür</span><span class="sxs-lookup"><span data-stu-id="8f784-110">Type</span></span>|<span data-ttu-id="8f784-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8f784-111">Runtime</span></span>|
