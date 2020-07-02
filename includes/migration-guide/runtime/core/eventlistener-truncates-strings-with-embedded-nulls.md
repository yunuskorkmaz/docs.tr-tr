---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620567"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="7245c-101">EventListener, gömülü null değerleri olan dizeleri keser</span><span class="sxs-lookup"><span data-stu-id="7245c-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="7245c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7245c-102">Details</span></span>

<span data-ttu-id="7245c-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>gömülü null değerleri olan dizeleri keser.</span><span class="sxs-lookup"><span data-stu-id="7245c-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="7245c-104">Null karakterler sınıf tarafından desteklenmiyor <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="7245c-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="7245c-105">Değişiklik yalnızca <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> işlemdeki verileri okumak için kullanılan uygulamaları etkiler <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> ve sınırlayıcı olarak null karakterler kullanır.</span><span class="sxs-lookup"><span data-stu-id="7245c-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7245c-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="7245c-106">Suggestion</span></span>

<span data-ttu-id="7245c-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>Mümkünse, gömülü null karakterleri kullanmamalıdır verilerin güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="7245c-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="7245c-108">Name</span><span class="sxs-lookup"><span data-stu-id="7245c-108">Name</span></span>    | <span data-ttu-id="7245c-109">Değer</span><span class="sxs-lookup"><span data-stu-id="7245c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7245c-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7245c-110">Scope</span></span>   |<span data-ttu-id="7245c-111">Edge</span><span class="sxs-lookup"><span data-stu-id="7245c-111">Edge</span></span>|
|<span data-ttu-id="7245c-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7245c-112">Version</span></span>|<span data-ttu-id="7245c-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7245c-113">4.5.1</span></span>|
|<span data-ttu-id="7245c-114">Tür</span><span class="sxs-lookup"><span data-stu-id="7245c-114">Type</span></span>|<span data-ttu-id="7245c-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7245c-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7245c-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7245c-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
