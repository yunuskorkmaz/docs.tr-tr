---
ms.openlocfilehash: 8964cd2f69e95e4078001997ad5a5d126ce42d7b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496556"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="7463f-101">KeyedCollection için veri bağlama geliştirmesi</span><span class="sxs-lookup"><span data-stu-id="7463f-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="7463f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7463f-102">Details</span></span>

<span data-ttu-id="7463f-103"><xref:System.Windows.Data.Binding>Kaynak nesne aynı imzaya sahip özel bir Dizin Oluşturucu (örneğin, KeyedCollection &lt; Int, TItem) bildirdiğinde, IList Indexer 'ın yanlış kullanımı düzeltildi &gt; .</span><span class="sxs-lookup"><span data-stu-id="7463f-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7463f-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="7463f-104">Suggestion</span></span>

<span data-ttu-id="7463f-105">Daha eski bir sürümü hedefleyen bir uygulamanın bu değişiklikten faydalanabilir olması için, .NET Framework 4,8 veya üzeri bir sürümde çalışmalıdır ve uygulama yapılandırma dosyasının bölümüne aşağıdaki [AppContext anahtarını](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) ekleyerek değişikliği kabul etmelidir <code>&lt;runtime&gt;</code> <code>false</code> :</span><span class="sxs-lookup"><span data-stu-id="7463f-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7463f-106">Name</span><span class="sxs-lookup"><span data-stu-id="7463f-106">Name</span></span>    | <span data-ttu-id="7463f-107">Değer</span><span class="sxs-lookup"><span data-stu-id="7463f-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7463f-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7463f-108">Scope</span></span>   |<span data-ttu-id="7463f-109">Ana</span><span class="sxs-lookup"><span data-stu-id="7463f-109">Major</span></span>|
|<span data-ttu-id="7463f-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7463f-110">Version</span></span>|<span data-ttu-id="7463f-111">4,8</span><span class="sxs-lookup"><span data-stu-id="7463f-111">4.8</span></span>|
|<span data-ttu-id="7463f-112">Tür</span><span class="sxs-lookup"><span data-stu-id="7463f-112">Type</span></span>|<span data-ttu-id="7463f-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7463f-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7463f-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7463f-114">Affected APIs</span></span>

<span data-ttu-id="7463f-115">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="7463f-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
