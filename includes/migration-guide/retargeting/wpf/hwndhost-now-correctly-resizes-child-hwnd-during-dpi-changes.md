---
ms.openlocfilehash: d374ded6a29ce815beeb26505010563a26d978e8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803564"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost artık doğru şekilde alt HWND DPI değişiklik sırasında yeniden boyutlandırır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümleri, WPF İzleyici başına uyumlu modda çalıştırdığınızda denetimleri barındırılan içinde <xref:System.Windows.Interop.HwndHost> doğru DPI değiştikten sonra gibi boyutta değil taşınırken uygulamalar bir izleyiciden diğerine. Bu düzeltme, barındırılan denetimleri uygun şekilde boyutlandırıldığından sağlar.|
|Öneri|Sırayla bu değişiklikleri yararlanmak uygulama için .NET Framework 4.7.2 çalıştırmanız gerekir veya sonraki bir sürümü ve bunun için bu davranışı aşağıdaki ayarlayarak katılımı gerekir [AppContext anahtar](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) içinde <code>&lt;runtime&gt;</code> uygulama yapılandırma bölümü Dosya <code>false</code>aşağıdaki örnekte gösterildiği gibi.<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Ana|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|

