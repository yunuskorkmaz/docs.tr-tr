---
ms.openlocfilehash: 5a96b40e5e0df6a47415acecab410444a713632b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496691"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="53ee9-101">ETW EventListeners açık anahtar sözcüklere sahip sağlayıcılardan olayları yakalamaz (TPL sağlayıcısı gibi)</span><span class="sxs-lookup"><span data-stu-id="53ee9-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

#### <a name="details"></a><span data-ttu-id="53ee9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="53ee9-102">Details</span></span>

<span data-ttu-id="53ee9-103">Boş bir anahtar sözcük maskesine sahip ETW EventListeners, açık anahtar sözcüklere sahip sağlayıcılardan olayları düzgün bir şekilde yakalamaz.</span><span class="sxs-lookup"><span data-stu-id="53ee9-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="53ee9-104">.NET Framework 4,5 ' de, TPL sağlayıcısı açık anahtar sözcükler sağlamaya başladı ve bu sorunu tetikledi.</span><span class="sxs-lookup"><span data-stu-id="53ee9-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="53ee9-105">.NET Framework 4,6 ' de EventListeners artık bu soruna sahip olmayacak şekilde güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="53ee9-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="53ee9-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="53ee9-106">Suggestion</span></span>

<span data-ttu-id="53ee9-107">Bu sorunu geçici olarak çözmek için, ile yapılan çağrıları, <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> &quot; kullanım için herhangi bir anahtar sözcük maskesini açıkça belirten EnableEvents aşırı yüklemesiyle değiştirin &quot; : <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code> . Alternatif olarak, bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükseltilerek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="53ee9-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="53ee9-108">Name</span><span class="sxs-lookup"><span data-stu-id="53ee9-108">Name</span></span>    | <span data-ttu-id="53ee9-109">Değer</span><span class="sxs-lookup"><span data-stu-id="53ee9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="53ee9-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="53ee9-110">Scope</span></span>   |<span data-ttu-id="53ee9-111">Edge</span><span class="sxs-lookup"><span data-stu-id="53ee9-111">Edge</span></span>|
|<span data-ttu-id="53ee9-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="53ee9-112">Version</span></span>|<span data-ttu-id="53ee9-113">4,5</span><span class="sxs-lookup"><span data-stu-id="53ee9-113">4.5</span></span>|
|<span data-ttu-id="53ee9-114">Tür</span><span class="sxs-lookup"><span data-stu-id="53ee9-114">Type</span></span>|<span data-ttu-id="53ee9-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="53ee9-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="53ee9-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="53ee9-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`

-->
