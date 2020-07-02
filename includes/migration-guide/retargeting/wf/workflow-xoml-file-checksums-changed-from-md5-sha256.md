---
ms.openlocfilehash: 2aa424ff5e3308b730c22cb865993d4100f193cc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616303"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="2fe3e-101">İş akışı XOML dosya sağlama toplamı, MD5 'den SHA256 'e değişti</span><span class="sxs-lookup"><span data-stu-id="2fe3e-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="2fe3e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2fe3e-102">Details</span></span>

<span data-ttu-id="2fe3e-103">Visual Studio ile XOML tabanlı iş akışlarının hatalarını ayıklamayı desteklemek için, XOML dosyalarını içeren iş akışı projeleri derleme oluştururken, XOML dosyası içeriğinin bir sağlama toplamı bir değer olarak oluşturulan koda dahil edilir <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2fe3e-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="2fe3e-104">.NET Framework 4.7.2 ve önceki sürümlerde, bu sağlama toplamı karma, FIPS özellikli sistemlerde sorunlara neden olan MD5 algoritmasını kullandı.</span><span class="sxs-lookup"><span data-stu-id="2fe3e-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="2fe3e-105">4,8 .NET Framework başlayarak kullanılan algoritma SHA256.</span><span class="sxs-lookup"><span data-stu-id="2fe3e-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="2fe3e-106">WorkflowMarkupSourceAttribute. MD5Digest ile compatibile olmak için, oluşturulan sağlama toplamı yalnızca ilk 16 bayt kullanılır. Bu, hata ayıklama sırasında sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fe3e-106">To be compatibile with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="2fe3e-107">Projenizi yeniden derlemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2fe3e-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2fe3e-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="2fe3e-108">Suggestion</span></span>

<span data-ttu-id="2fe3e-109">Projenizin yeniden oluşturulması sorunu çözmezse, `AppContext` &quot;Switch.SysDıtem. Workflow. ComponentModel. UseLegacyHashForXomlFileChecksum anahtarını &quot; true olarak ayarlamayı deneyin. Kodda:</span><span class="sxs-lookup"><span data-stu-id="2fe3e-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="2fe3e-110">Ya da bir yapılandırma dosyasında (Bu, kullanmakta olduğunuz MSBuild.exe için MSBuild.exe.config olması gerekir):</span><span class="sxs-lookup"><span data-stu-id="2fe3e-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2fe3e-111">Name</span><span class="sxs-lookup"><span data-stu-id="2fe3e-111">Name</span></span>    | <span data-ttu-id="2fe3e-112">Değer</span><span class="sxs-lookup"><span data-stu-id="2fe3e-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2fe3e-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2fe3e-113">Scope</span></span>   | <span data-ttu-id="2fe3e-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="2fe3e-114">Minor</span></span>       |
| <span data-ttu-id="2fe3e-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2fe3e-115">Version</span></span> | <span data-ttu-id="2fe3e-116">4,8</span><span class="sxs-lookup"><span data-stu-id="2fe3e-116">4.8</span></span>         |
| <span data-ttu-id="2fe3e-117">Tür</span><span class="sxs-lookup"><span data-stu-id="2fe3e-117">Type</span></span>    | <span data-ttu-id="2fe3e-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="2fe3e-118">Retargeting</span></span> |
