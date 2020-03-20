---
ms.openlocfilehash: 8aae403e3f23d3bfc755140b2ac29d757f10f753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74451600"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>KeyedCollection için Veri Bağlama geliştirme

|   |   |
|---|---|
|Ayrıntılar|Kaynak <xref:System.Windows.Data.Binding> nesne aynı imzaya sahip özel bir dizinleyici beyan ettiğinde IList dizinleyicisinin yanlış kullanımı düzeltildi (örneğin, KeyedCollection&lt;int,TItem).&gt;|
|Öneri|Eski bir sürümün bu değişiklikten yararlanabilmesi için .NET Framework 4.8 veya sonraki sürümlerde çalışması gerekir ve aşağıdaki [AppContext anahtarını](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) <code>&lt;runtime&gt;</code> uygulama config dosyasının bölümüne <code>false</code>ekleyerek ve şu şekilde ayarlayarak değişikliği tercih etmelidir:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Ana|
|Sürüm|4.8|
|Tür|Çalışma Zamanı|
