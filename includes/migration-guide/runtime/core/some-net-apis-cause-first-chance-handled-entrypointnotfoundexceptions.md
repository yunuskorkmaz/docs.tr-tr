---
ms.openlocfilehash: 6431f3b4d0983c44629e4fe760c75adcc277ddd4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497198"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="8d4b4-101">Bazı .NET API 'Leri ilk şans (işlenmiş) EntryPointNotFoundExceptions olur</span><span class="sxs-lookup"><span data-stu-id="8d4b4-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="8d4b4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8d4b4-102">Details</span></span>

<span data-ttu-id="8d4b4-103">.NET Framework 4,5 ' de, az sayıda .NET yöntemi ilk şans sunmaya başladı <xref:System.EntryPointNotFoundException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="8d4b4-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="8d4b4-104">Bu özel durumlar .NET Framework içinde işlendi, ancak ilk fırsat özel durumlarını beklememiş olan test otomasyonunu kesintiye uğratacaktır.</span><span class="sxs-lookup"><span data-stu-id="8d4b4-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="8d4b4-105">Bu aynı API 'Ler, HighVersionLie etkinken bazı ApiVerifier senaryolarını keser.</span><span class="sxs-lookup"><span data-stu-id="8d4b4-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8d4b4-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="8d4b4-106">Suggestion</span></span>

<span data-ttu-id="8d4b4-107">.NET Framework 4.5.1 ' e yükselterek bu hataya kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d4b4-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="8d4b4-108">Alternatif olarak, test Otomasyonu ilk şans üzerinde kesintiye uğramayan şekilde güncelleştirilemeyebilir <xref:System.EntryPointNotFoundException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="8d4b4-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="8d4b4-109">Name</span><span class="sxs-lookup"><span data-stu-id="8d4b4-109">Name</span></span>    | <span data-ttu-id="8d4b4-110">Değer</span><span class="sxs-lookup"><span data-stu-id="8d4b4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8d4b4-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8d4b4-111">Scope</span></span>   |<span data-ttu-id="8d4b4-112">Edge</span><span class="sxs-lookup"><span data-stu-id="8d4b4-112">Edge</span></span>|
|<span data-ttu-id="8d4b4-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8d4b4-113">Version</span></span>|<span data-ttu-id="8d4b4-114">4,5</span><span class="sxs-lookup"><span data-stu-id="8d4b4-114">4.5</span></span>|
|<span data-ttu-id="8d4b4-115">Tür</span><span class="sxs-lookup"><span data-stu-id="8d4b4-115">Type</span></span>|<span data-ttu-id="8d4b4-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="8d4b4-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8d4b4-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8d4b4-117">Affected APIs</span></span>

- <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)>

<!--

#### Affected APIs

- `M:System.Diagnostics.Debug.Assert(System.Boolean)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])`
- `M:System.Xml.Serialization.XmlSerializer.#ctor(System.Type)`

-->
