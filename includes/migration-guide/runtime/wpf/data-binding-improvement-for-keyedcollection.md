---
ms.openlocfilehash: 8964cd2f69e95e4078001997ad5a5d126ce42d7b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496556"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>KeyedCollection için veri bağlama geliştirmesi

#### <a name="details"></a>Ayrıntılar

<xref:System.Windows.Data.Binding>Kaynak nesne aynı imzaya sahip özel bir Dizin Oluşturucu (örneğin, KeyedCollection &lt; Int, TItem) bildirdiğinde, IList Indexer 'ın yanlış kullanımı düzeltildi &gt; .

#### <a name="suggestion"></a>Öneri

Daha eski bir sürümü hedefleyen bir uygulamanın bu değişiklikten faydalanabilir olması için, .NET Framework 4,8 veya üzeri bir sürümde çalışmalıdır ve uygulama yapılandırma dosyasının bölümüne aşağıdaki [AppContext anahtarını](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) ekleyerek değişikliği kabul etmelidir <code>&lt;runtime&gt;</code> <code>false</code> :<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Ana|
|Sürüm|4,8|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
