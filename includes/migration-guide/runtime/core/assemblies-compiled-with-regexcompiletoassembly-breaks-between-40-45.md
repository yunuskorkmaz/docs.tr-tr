---
ms.openlocfilehash: 424872b25436c7fcbe603639028e813eed6f9b99
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497556"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="45d64-101">4,0 ile 4,5 arasında Regex. CompileToAssembly sonları ile derlenen derlemeler</span><span class="sxs-lookup"><span data-stu-id="45d64-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="45d64-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="45d64-102">Details</span></span>

<span data-ttu-id="45d64-103">Derlenmiş normal ifadelerin bir derlemesi .NET Framework 4,5 ile derlenirse, ancak .NET Framework 4 ' ü hedefliyorsa, bu derlemede bulunan ve .NET Framework 4 yüklü olan bir sistemdeki normal ifadelerden birini kullanmaya çalışmak bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45d64-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="45d64-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="45d64-104">Suggestion</span></span>

<span data-ttu-id="45d64-105">Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="45d64-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="45d64-106">.NET Framework 4 ile normal ifadeleri içeren derlemeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="45d64-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="45d64-107">Yorumlanan bir normal ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="45d64-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="45d64-108">Name</span><span class="sxs-lookup"><span data-stu-id="45d64-108">Name</span></span>    | <span data-ttu-id="45d64-109">Değer</span><span class="sxs-lookup"><span data-stu-id="45d64-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="45d64-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="45d64-110">Scope</span></span>   |<span data-ttu-id="45d64-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="45d64-111">Minor</span></span>|
|<span data-ttu-id="45d64-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="45d64-112">Version</span></span>|<span data-ttu-id="45d64-113">4,5</span><span class="sxs-lookup"><span data-stu-id="45d64-113">4.5</span></span>|
|<span data-ttu-id="45d64-114">Tür</span><span class="sxs-lookup"><span data-stu-id="45d64-114">Type</span></span>|<span data-ttu-id="45d64-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="45d64-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="45d64-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="45d64-116">Affected APIs</span></span>

- <xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)`
- `M:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])`
- `M:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)`

-->
