---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616312"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost artık DPı değişiklikler sırasında alt HWND 'yi doğru şekilde yeniden boyutlandırır

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2 ve önceki sürümlerde, WPF, Izleyici ile uyumlu modda çalıştırıldığında, içinde barındırılan denetimler, <xref:System.Windows.Interop.HwndHost> uygulamaları bir izleyiciden diğerine taşırken olduğu gibi, DPI değişikliklerinden sonra düzgün şekilde boyutlandırılmaz. Bu düzeltilme, barındırılan denetimlerin uygun şekilde boyutlandırılmasını sağlar.

#### <a name="suggestion"></a>Öneri

Uygulamanın bu değişikliklerden faydalanabilir olması için, .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır ve [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) `<runtime>` `false` Aşağıdaki örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümünde aşağıdaki AppContext anahtarını ayarlayarak bu davranışı kabul etmelidir.

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4,8         |
| Tür    | Yeniden Hedefleme |
