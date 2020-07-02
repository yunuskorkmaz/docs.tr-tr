---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620574"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="abbed-101">EventSource. WriteEvent IMPLS 'ın aynı parametreleri aldığı aynı parametreleri (artı ID) iletmeli olması gerekir</span><span class="sxs-lookup"><span data-stu-id="abbed-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

#### <a name="details"></a><span data-ttu-id="abbed-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="abbed-102">Details</span></span>

<span data-ttu-id="abbed-103">Çalışma zamanı şimdi aşağıdakileri belirten sözleşmeyi zorluyor: <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> BIR ETW olay yöntemi tanımlayan öğesinden türetilmiş bir sınıf, <code>EventSource.WriteEvent</code> olay kimliği ile bırlıkte, ETW olay yönteminin geçirildiği bağımsız değişkenlerle birlikte temel sınıf metodunu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abbed-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="abbed-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="abbed-104">Suggestion</span></span>

<span data-ttu-id="abbed-105"><xref:System.IndexOutOfRangeException?displayProperty=fullName> <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> Bu sözleşmeyi ihlal eden bir olay kaynağı için işlemdeki verileri okuduğunda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="abbed-105">An <xref:System.IndexOutOfRangeException?displayProperty=fullName> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process for an event source that violates this contract.</span></span>

| <span data-ttu-id="abbed-106">Name</span><span class="sxs-lookup"><span data-stu-id="abbed-106">Name</span></span>    | <span data-ttu-id="abbed-107">Değer</span><span class="sxs-lookup"><span data-stu-id="abbed-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="abbed-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="abbed-108">Scope</span></span>   |<span data-ttu-id="abbed-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="abbed-109">Minor</span></span>|
|<span data-ttu-id="abbed-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="abbed-110">Version</span></span>|<span data-ttu-id="abbed-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="abbed-111">4.5.1</span></span>|
|<span data-ttu-id="abbed-112">Tür</span><span class="sxs-lookup"><span data-stu-id="abbed-112">Type</span></span>|<span data-ttu-id="abbed-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="abbed-113">Runtime</span></span>|
