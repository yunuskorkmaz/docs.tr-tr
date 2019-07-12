---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802706"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="70701-101">Veri bağlama geliştirme KeyedCollection için</span><span class="sxs-lookup"><span data-stu-id="70701-101">Data Binding improvement for KeyedCollection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="70701-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="70701-102">Details</span></span>|<span data-ttu-id="70701-103">Sabit <xref:System.Windows.Data.Binding> kaynak nesnesi aynı imzaya sahip özel bir dizin oluşturucu bildirir, IList Indexer'ın yanlış kullanımı (örneğin KeyedCollection&lt;int, TItem&gt;).</span><span class="sxs-lookup"><span data-stu-id="70701-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (e.g. KeyedCollection&lt;int,TItem&gt;).</span></span>|
|<span data-ttu-id="70701-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="70701-104">Suggestion</span></span>|<span data-ttu-id="70701-105">Sırayla bu değişiklik yararlanmak uygulama için .NET Framework 4.7.2 çalıştırmanız gerekir veya sonraki bir sürümü ve bu değişiklik aşağıdaki ekleyerek kabul et gerekir [AppContext anahtar](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) için <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasının ve Bu ayarın <code>false</code>:</span><span class="sxs-lookup"><span data-stu-id="70701-105">In order for the application to benefit from this change, it must run on the .NET Framework 4.7.2 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="70701-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="70701-106">Scope</span></span>|<span data-ttu-id="70701-107">Ana</span><span class="sxs-lookup"><span data-stu-id="70701-107">Major</span></span>|
|<span data-ttu-id="70701-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="70701-108">Version</span></span>|<span data-ttu-id="70701-109">4.8</span><span class="sxs-lookup"><span data-stu-id="70701-109">4.8</span></span>|
|<span data-ttu-id="70701-110">Tür</span><span class="sxs-lookup"><span data-stu-id="70701-110">Type</span></span>|<span data-ttu-id="70701-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="70701-111">Runtime</span></span>|

