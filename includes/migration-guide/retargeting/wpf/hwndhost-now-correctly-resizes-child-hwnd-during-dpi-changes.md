---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616312"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="a1039-101">HwndHost artık DPı değişiklikler sırasında alt HWND 'yi doğru şekilde yeniden boyutlandırır</span><span class="sxs-lookup"><span data-stu-id="a1039-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="a1039-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a1039-102">Details</span></span>

<span data-ttu-id="a1039-103">.NET Framework 4.7.2 ve önceki sürümlerde, WPF, Izleyici ile uyumlu modda çalıştırıldığında, içinde barındırılan denetimler, <xref:System.Windows.Interop.HwndHost> uygulamaları bir izleyiciden diğerine taşırken olduğu gibi, DPI değişikliklerinden sonra düzgün şekilde boyutlandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="a1039-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="a1039-104">Bu düzeltilme, barındırılan denetimlerin uygun şekilde boyutlandırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1039-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a1039-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="a1039-105">Suggestion</span></span>

<span data-ttu-id="a1039-106">Uygulamanın bu değişikliklerden faydalanabilir olması için, .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır ve [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) `<runtime>` `false` Aşağıdaki örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümünde aşağıdaki AppContext anahtarını ayarlayarak bu davranışı kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="a1039-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="a1039-107">Name</span><span class="sxs-lookup"><span data-stu-id="a1039-107">Name</span></span>    | <span data-ttu-id="a1039-108">Değer</span><span class="sxs-lookup"><span data-stu-id="a1039-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a1039-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a1039-109">Scope</span></span>   | <span data-ttu-id="a1039-110">Ana</span><span class="sxs-lookup"><span data-stu-id="a1039-110">Major</span></span>       |
| <span data-ttu-id="a1039-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1039-111">Version</span></span> | <span data-ttu-id="a1039-112">4,8</span><span class="sxs-lookup"><span data-stu-id="a1039-112">4.8</span></span>         |
| <span data-ttu-id="a1039-113">Tür</span><span class="sxs-lookup"><span data-stu-id="a1039-113">Type</span></span>    | <span data-ttu-id="a1039-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="a1039-114">Retargeting</span></span> |
