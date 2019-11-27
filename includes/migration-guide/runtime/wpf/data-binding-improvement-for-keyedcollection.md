---
ms.openlocfilehash: 8aae403e3f23d3bfc755140b2ac29d757f10f753
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451600"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>KeyedCollection için veri bağlama geliştirmesi

|   |   |
|---|---|
|Ayrıntılar|Sabit <xref:System.Windows.Data.Binding>, kaynak nesne aynı imzaya sahip özel bir Dizin Oluşturucu (örneğin, KeyedCollection&lt;int, TItem&gt;) bildirdiğinde IList Indexer 'ın yanlış kullanımı.|
|Öneri|Eski bir sürümü hedefleyen bir uygulamanın bu değişiklikten faydalanabilir olması için, .NET Framework 4,8 veya üzeri bir sürümde çalışmalıdır ve uygulama yapılandırma dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdaki [AppContext anahtarını](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) ekleyerek değişikliği kabul etmelidir ve bunu <code>false</code>olarak ayarlayarak:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|düzeltme sınıfı,|
|Sürüm|4.8|
|Type|Çalışma zamanı|
