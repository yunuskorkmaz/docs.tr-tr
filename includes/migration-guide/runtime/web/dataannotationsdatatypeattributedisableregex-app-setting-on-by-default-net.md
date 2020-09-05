---
ms.openlocfilehash: 0d38e2177377e7e9ea911071eb65aa13aa1f5900
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497044"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a><span data-ttu-id="1fdd9-101">"Dataaçıklamalarda: dataTypeAttribute: disableRegEx" uygulama ayarı, .NET Framework 4.7.2 içinde varsayılan olarak açık</span><span class="sxs-lookup"><span data-stu-id="1fdd9-101">"dataAnnotations:dataTypeAttribute:disableRegEx" app setting is on by default in .NET Framework 4.7.2</span></span>

#### <a name="details"></a><span data-ttu-id="1fdd9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1fdd9-102">Details</span></span>

<span data-ttu-id="1fdd9-103">.NET Framework 4.6.1 ' de, <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> kullanıcıların veri türü özniteliklerinde (, ve gibi) normal ifadelerin kullanımını devre dışı bırakmasına olanak tanıyan bir uygulama ayarı () sunuldu <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1fdd9-103">In .NET Framework 4.6.1, an app setting (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) was introduced that allows users to disable the use of regular expressions in data type attributes (such as <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, and <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="1fdd9-104">Bu, belirli normal ifadeleri kullanarak hizmet reddi saldırısı olasılığa karşı güvenlik açığını azaltmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1fdd9-104">This helps to reduce security vulnerability such as avoiding the possibility of a Denial of Service attack using specific regular expressions.</span></span><br/><span data-ttu-id="1fdd9-105">.NET Framework 4.6.1 ' de, RegEx kullanımını devre dışı bırakmak için bu uygulama ayarı <code>false</code> Varsayılan olarak olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1fdd9-105">In .NET Framework 4.6.1, this app setting to disable RegEx usage was set to <code>false</code> by default.</span></span> <span data-ttu-id="1fdd9-106">.NET Framework 4.7.2 ile başlayarak, bu yapılandırma anahtarı <code>true</code> Varsayılan olarak, .NET Framework 4.7.2 ve üstünü hedefleyen web uygulamalarına yönelik güvenli güvenlik açığını azaltmak için varsayılan olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1fdd9-106">Starting with .NET Framework 4.7.2, this config switch is set to <code>true</code> by default to further reduce secure vulnerability for web applications that target .NET Framework 4.7.2 and above.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1fdd9-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="1fdd9-107">Suggestion</span></span>

<span data-ttu-id="1fdd9-108">Web uygulamanızdaki normal ifadelerin .NET Framework 4.7.2 'e yükselttikten sonra çalışmadıysanız, <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> <code>false</code> önceki davranışa geri dönmek için ayarının değerini olarak güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fdd9-108">If you find that regular expressions in your web application do not work after upgrading to .NET Framework 4.7.2, you can update the value of the <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> setting to <code>false</code> to revert to the previous behavior.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1fdd9-109">Name</span><span class="sxs-lookup"><span data-stu-id="1fdd9-109">Name</span></span>    | <span data-ttu-id="1fdd9-110">Değer</span><span class="sxs-lookup"><span data-stu-id="1fdd9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1fdd9-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1fdd9-111">Scope</span></span>   |<span data-ttu-id="1fdd9-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="1fdd9-112">Minor</span></span>|
|<span data-ttu-id="1fdd9-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1fdd9-113">Version</span></span>|<span data-ttu-id="1fdd9-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="1fdd9-114">4.7.2</span></span>|
|<span data-ttu-id="1fdd9-115">Tür</span><span class="sxs-lookup"><span data-stu-id="1fdd9-115">Type</span></span>|<span data-ttu-id="1fdd9-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="1fdd9-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1fdd9-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1fdd9-117">Affected APIs</span></span>

<span data-ttu-id="1fdd9-118">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="1fdd9-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
