---
ms.openlocfilehash: b92086c8ccf7592ce70b75bd31d4ea255c35b543
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803564"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost şimdi doğru DPI değişiklikleri sırasında çocuk-HWND yeniden boyutlar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerde, WPF'nin İzleme Başına <xref:System.Windows.Interop.HwndHost> Farkında modunda çalıştırıldığı önceki sürümlerde, dpi değişikliklerden sonra barındırılan denetimler, uygulamaları bir monitörden diğerine taşımak gibi doğru boyutlandırılmadı. Bu düzeltme, barındırılan denetimlerin uygun şekilde boyutlandırılmasını sağlar.|
|Öneri|Uygulamanın bu değişikliklerden yararlanabilmesi için .NET Framework 4.7.2 veya daha sonra üzerinde çalışması ve aşağıdaki örnekte görüldüğü gibi, <code>&lt;runtime&gt;</code> uygulama config dosyasının <code>false</code>bölümünde aşağıdaki [AppContext Switch'i](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) ayarlayarak bu davranışı seçmesi gerekir.<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Ana|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|
