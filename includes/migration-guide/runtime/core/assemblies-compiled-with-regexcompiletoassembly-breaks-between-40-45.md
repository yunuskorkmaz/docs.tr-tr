---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620551"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="bf631-101">4,0 ile 4,5 arasında Regex. CompileToAssembly sonları ile derlenen derlemeler</span><span class="sxs-lookup"><span data-stu-id="bf631-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="bf631-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bf631-102">Details</span></span>

<span data-ttu-id="bf631-103">Derlenmiş normal ifadelerin bir derlemesi .NET Framework 4,5 ile derlenirse, ancak .NET Framework 4 ' ü hedefliyorsa, bu derlemede bulunan ve .NET Framework 4 yüklü olan bir sistemdeki normal ifadelerden birini kullanmaya çalışmak bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf631-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bf631-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="bf631-104">Suggestion</span></span>

<span data-ttu-id="bf631-105">Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf631-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="bf631-106">.NET Framework 4 ile normal ifadeleri içeren derlemeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf631-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="bf631-107">Yorumlanan bir normal ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf631-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="bf631-108">Name</span><span class="sxs-lookup"><span data-stu-id="bf631-108">Name</span></span>    | <span data-ttu-id="bf631-109">Değer</span><span class="sxs-lookup"><span data-stu-id="bf631-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bf631-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bf631-110">Scope</span></span>   |<span data-ttu-id="bf631-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="bf631-111">Minor</span></span>|
|<span data-ttu-id="bf631-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bf631-112">Version</span></span>|<span data-ttu-id="bf631-113">4,5</span><span class="sxs-lookup"><span data-stu-id="bf631-113">4.5</span></span>|
|<span data-ttu-id="bf631-114">Tür</span><span class="sxs-lookup"><span data-stu-id="bf631-114">Type</span></span>|<span data-ttu-id="bf631-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="bf631-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bf631-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bf631-116">Affected APIs</span></span>

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
