---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616296"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a><span data-ttu-id="19ddc-101">İş akışı XOML tanımı ve SqlTrackingService önbellek anahtarları MD5 'den SHA256 'e değişti</span><span class="sxs-lookup"><span data-stu-id="19ddc-101">Workflow XOML definition and SqlTrackingService cache keys changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="19ddc-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="19ddc-102">Details</span></span>

<span data-ttu-id="19ddc-103">' Deki Iş akışı çalışma zamanı, XOML içinde tanımlanan iş akışı tanımlarının bir önbelleğini tutar.</span><span class="sxs-lookup"><span data-stu-id="19ddc-103">The Workflow Runtime in keeps a cache of workflow definitions defined in XOML.</span></span> <span data-ttu-id="19ddc-104">SqlTrackingService, dizeler tarafından girilen bir önbelleği de tutar.</span><span class="sxs-lookup"><span data-stu-id="19ddc-104">The SqlTrackingService also keeps a cache that is keyed by strings.</span></span> <span data-ttu-id="19ddc-105">Bu önbellekler, sağlama toplamı karma değeri içeren değerlere göre anahtarlanır.</span><span class="sxs-lookup"><span data-stu-id="19ddc-105">These caches are keyed by values that include checksum hash value.</span></span> <span data-ttu-id="19ddc-106">.NET Framework 4.7.2 ve önceki sürümlerde, bu sağlama toplamı karma, FIPS özellikli sistemlerde sorunlara neden olan MD5 algoritmasını kullandı.</span><span class="sxs-lookup"><span data-stu-id="19ddc-106">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="19ddc-107">4,8 .NET Framework başlayarak kullanılan algoritma SHA256. Bu değişiklik ile bir uyumluluk sorunu olmaması gerekir, çünkü Iş akışı çalışma zamanı ve SqlTrackingService her başlatıldığında değerler yeniden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="19ddc-107">Starting with the .NET Framework 4.8, the algorithm used is SHA256.There shouldn't be a compatibility issue with this change because the values are recalculated each time the Workflow Runtime and SqlTrackingService is started.</span></span> <span data-ttu-id="19ddc-108">Bununla birlikte, müşterilerin, gerekirse eski karma algoritmanın kullanımına geri dönüşmesini sağlayan bir olağandışı şekilde sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="19ddc-108">However, we have provided quirks to allow customers to revert back to usage of the legacy hashing algorithm, if necessary.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="19ddc-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="19ddc-109">Suggestion</span></span>

<span data-ttu-id="19ddc-110">Bu değişiklik iş akışlarını yürütürken bir sorun yaparsa, anahtarların birini veya her ikisini ayarlamayı deneyin `AppContext` :</span><span class="sxs-lookup"><span data-stu-id="19ddc-110">If this change presents a problem when executing workflows, try setting one or both of the `AppContext` switches:</span></span>

- <span data-ttu-id="19ddc-111">&quot;Switch.SysTem. Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey &quot; true.</span><span class="sxs-lookup"><span data-stu-id="19ddc-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</span></span>
- <span data-ttu-id="19ddc-112">&quot;Switch.SysTem. Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey &quot; true.</span><span class="sxs-lookup"><span data-stu-id="19ddc-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</span></span>
<span data-ttu-id="19ddc-113">Kod:</span><span class="sxs-lookup"><span data-stu-id="19ddc-113">In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="19ddc-114">Ya da yapılandırma dosyasında (Bu nesneyi oluşturan uygulamanın yapılandırma dosyasında olması gerekir <xref:System.Workflow.Runtime.WorkflowRuntime> ):</span><span class="sxs-lookup"><span data-stu-id="19ddc-114">Or in the configuration file (this needs to be in the config file for the application that is creating the <xref:System.Workflow.Runtime.WorkflowRuntime> object):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="19ddc-115">Name</span><span class="sxs-lookup"><span data-stu-id="19ddc-115">Name</span></span>    | <span data-ttu-id="19ddc-116">Değer</span><span class="sxs-lookup"><span data-stu-id="19ddc-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="19ddc-117">Kapsam</span><span class="sxs-lookup"><span data-stu-id="19ddc-117">Scope</span></span>   | <span data-ttu-id="19ddc-118">İkincil</span><span class="sxs-lookup"><span data-stu-id="19ddc-118">Minor</span></span>       |
| <span data-ttu-id="19ddc-119">Sürüm</span><span class="sxs-lookup"><span data-stu-id="19ddc-119">Version</span></span> | <span data-ttu-id="19ddc-120">4,8</span><span class="sxs-lookup"><span data-stu-id="19ddc-120">4.8</span></span>         |
| <span data-ttu-id="19ddc-121">Tür</span><span class="sxs-lookup"><span data-stu-id="19ddc-121">Type</span></span>    | <span data-ttu-id="19ddc-122">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="19ddc-122">Retargeting</span></span> |
