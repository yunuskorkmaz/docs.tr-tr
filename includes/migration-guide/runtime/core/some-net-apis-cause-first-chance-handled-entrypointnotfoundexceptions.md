---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622142"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="0e5e3-101">Bazı .NET API 'Leri ilk şans (işlenmiş) EntryPointNotFoundExceptions olur</span><span class="sxs-lookup"><span data-stu-id="0e5e3-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="0e5e3-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0e5e3-102">Details</span></span>

<span data-ttu-id="0e5e3-103">.NET Framework 4,5 ' de, az sayıda .NET yöntemi ilk şans sunmaya başladı <xref:System.EntryPointNotFoundException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="0e5e3-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="0e5e3-104">Bu özel durumlar .NET Framework içinde işlendi, ancak ilk fırsat özel durumlarını beklememiş olan test otomasyonunu kesintiye uğratacaktır.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="0e5e3-105">Bu aynı API 'Ler, HighVersionLie etkinken bazı ApiVerifier senaryolarını keser.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0e5e3-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="0e5e3-106">Suggestion</span></span>

<span data-ttu-id="0e5e3-107">.NET Framework 4.5.1 ' e yükselterek bu hataya kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="0e5e3-108">Alternatif olarak, test Otomasyonu ilk şans üzerinde kesintiye uğramayan şekilde güncelleştirilemeyebilir <xref:System.EntryPointNotFoundException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="0e5e3-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="0e5e3-109">Name</span><span class="sxs-lookup"><span data-stu-id="0e5e3-109">Name</span></span>    | <span data-ttu-id="0e5e3-110">Değer</span><span class="sxs-lookup"><span data-stu-id="0e5e3-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0e5e3-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0e5e3-111">Scope</span></span>   |<span data-ttu-id="0e5e3-112">Edge</span><span class="sxs-lookup"><span data-stu-id="0e5e3-112">Edge</span></span>|
|<span data-ttu-id="0e5e3-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0e5e3-113">Version</span></span>|<span data-ttu-id="0e5e3-114">4,5</span><span class="sxs-lookup"><span data-stu-id="0e5e3-114">4.5</span></span>|
|<span data-ttu-id="0e5e3-115">Tür</span><span class="sxs-lookup"><span data-stu-id="0e5e3-115">Type</span></span>|<span data-ttu-id="0e5e3-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="0e5e3-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e5e3-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0e5e3-117">Affected APIs</span></span>

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
