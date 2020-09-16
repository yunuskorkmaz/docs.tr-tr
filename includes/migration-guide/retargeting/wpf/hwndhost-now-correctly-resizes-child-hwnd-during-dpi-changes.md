---
ms.openlocfilehash: 77e231f8ef1dde8a263b8622311099a4a404062d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606179"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="8f3e0-101">HwndHost artık DPı değişiklikler sırasında alt HWND 'yi doğru şekilde yeniden boyutlandırır</span><span class="sxs-lookup"><span data-stu-id="8f3e0-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="8f3e0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8f3e0-102">Details</span></span>

<span data-ttu-id="8f3e0-103">.NET Framework 4.7.2 ve önceki sürümlerde, WPF, Izleyici ile uyumlu modda çalıştırıldığında, içinde barındırılan denetimler, <xref:System.Windows.Interop.HwndHost> uygulamaları bir izleyiciden diğerine taşırken olduğu gibi, DPI değişikliklerinden sonra düzgün şekilde boyutlandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="8f3e0-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="8f3e0-104">Bu düzeltilme, barındırılan denetimlerin uygun şekilde boyutlandırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f3e0-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8f3e0-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="8f3e0-105">Suggestion</span></span>

<span data-ttu-id="8f3e0-106">Uygulamanın bu değişikliklerden faydalanabilir olması için, .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır ve [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` `false` Aşağıdaki örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümünde aşağıdaki AppContext anahtarını ayarlayarak bu davranışı kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="8f3e0-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="8f3e0-107">Name</span><span class="sxs-lookup"><span data-stu-id="8f3e0-107">Name</span></span>    | <span data-ttu-id="8f3e0-108">Değer</span><span class="sxs-lookup"><span data-stu-id="8f3e0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8f3e0-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8f3e0-109">Scope</span></span>   | <span data-ttu-id="8f3e0-110">Ana</span><span class="sxs-lookup"><span data-stu-id="8f3e0-110">Major</span></span>       |
| <span data-ttu-id="8f3e0-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8f3e0-111">Version</span></span> | <span data-ttu-id="8f3e0-112">4,8</span><span class="sxs-lookup"><span data-stu-id="8f3e0-112">4.8</span></span>         |
| <span data-ttu-id="8f3e0-113">Tür</span><span class="sxs-lookup"><span data-stu-id="8f3e0-113">Type</span></span>    | <span data-ttu-id="8f3e0-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="8f3e0-114">Retargeting</span></span> |
