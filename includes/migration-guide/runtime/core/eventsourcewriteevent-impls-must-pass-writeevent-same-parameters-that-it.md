---
ms.openlocfilehash: 99a7fa0fcfce6d490a182f85709b5dd0e0e8c86f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497775"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="a9856-101">EventSource. WriteEvent IMPLS 'ın aynı parametreleri aldığı aynı parametreleri (artı ID) iletmeli olması gerekir</span><span class="sxs-lookup"><span data-stu-id="a9856-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

#### <a name="details"></a><span data-ttu-id="a9856-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a9856-102">Details</span></span>

<span data-ttu-id="a9856-103">Çalışma zamanı şimdi aşağıdakileri belirten sözleşmeyi zorluyor: <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> BIR ETW olay yöntemi tanımlayan öğesinden türetilmiş bir sınıf, <code>EventSource.WriteEvent</code> olay kimliği ile bırlıkte, ETW olay yönteminin geçirildiği bağımsız değişkenlerle birlikte temel sınıf metodunu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9856-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a9856-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="a9856-104">Suggestion</span></span>

<span data-ttu-id="a9856-105"><xref:System.IndexOutOfRangeException?displayProperty=fullName> <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> Bu sözleşmeyi ihlal eden bir olay kaynağı için işlemdeki verileri okuduğunda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a9856-105">An <xref:System.IndexOutOfRangeException?displayProperty=fullName> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process for an event source that violates this contract.</span></span>

| <span data-ttu-id="a9856-106">Name</span><span class="sxs-lookup"><span data-stu-id="a9856-106">Name</span></span>    | <span data-ttu-id="a9856-107">Değer</span><span class="sxs-lookup"><span data-stu-id="a9856-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a9856-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a9856-108">Scope</span></span>   |<span data-ttu-id="a9856-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="a9856-109">Minor</span></span>|
|<span data-ttu-id="a9856-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a9856-110">Version</span></span>|<span data-ttu-id="a9856-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="a9856-111">4.5.1</span></span>|
|<span data-ttu-id="a9856-112">Tür</span><span class="sxs-lookup"><span data-stu-id="a9856-112">Type</span></span>|<span data-ttu-id="a9856-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="a9856-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a9856-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a9856-114">Affected APIs</span></span>

<span data-ttu-id="a9856-115">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="a9856-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
