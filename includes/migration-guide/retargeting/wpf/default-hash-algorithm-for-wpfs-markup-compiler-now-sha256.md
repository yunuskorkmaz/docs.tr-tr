---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614927"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a><span data-ttu-id="80fa2-101">WPF 'in biçimlendirme derleyicisi için varsayılan karma algoritması artık SHA256</span><span class="sxs-lookup"><span data-stu-id="80fa2-101">The default hash algorithm for WPF's Markup Compiler is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="80fa2-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="80fa2-102">Details</span></span>

<span data-ttu-id="80fa2-103">WPF MarkupCompiler, XAML işaretleme dosyaları için derleme hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="80fa2-103">The WPF MarkupCompiler provides compilation services for XAML markup files.</span></span>  <span data-ttu-id="80fa2-104">.NET Framework 4.7.1 ve önceki sürümlerde, sağlama toplamı için kullanılan varsayılan karma algoritma SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="80fa2-104">In the .NET Framework 4.7.1 and earlier versions, the default hash algorithm used for checksums was SHA1.</span></span> <span data-ttu-id="80fa2-105">SHA1 ile ilgili en son güvenlik sorunları nedeniyle, bu varsayılan değer .NET Framework 4.7.2 ile başlayarak SHA256 olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="80fa2-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.2.</span></span>  <span data-ttu-id="80fa2-106">Bu değişiklik, derleme sırasında biçimlendirme dosyaları için tüm sağlama toplamı üretimini etkiler.</span><span class="sxs-lookup"><span data-stu-id="80fa2-106">This change affects all checksum generation for markup files during compilation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="80fa2-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="80fa2-107">Suggestion</span></span>

<span data-ttu-id="80fa2-108">.NET Framework 4.7.2 veya üstünü hedefleyen ve SHA1 karma davranışına geri dönmek isteyen bir geliştirici, aşağıdaki AppContext bayrağını ayarlamış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80fa2-108">A developer who targets .NET Framework 4.7.2 or greater and wants to revert to SHA1 hashing behavior must set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="80fa2-109">.NET 4.7.2 'ın altında bir Framework sürümünü hedeflerken SHA256 karmasını kullanmak isteyen bir geliştirici aşağıdaki AppContext bayrağını ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="80fa2-109">A developer who wants to utilize SHA256 hashing while targeting a framework version below .NET 4.7.2 must set the below AppContext flag.</span></span>  <span data-ttu-id="80fa2-110">.NET Framework yüklü sürümünün 4.7.2 veya daha büyük olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="80fa2-110">Note that the installed version of the .NET Framework must be 4.7.2 or greater.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="80fa2-111">Name</span><span class="sxs-lookup"><span data-stu-id="80fa2-111">Name</span></span>    | <span data-ttu-id="80fa2-112">Değer</span><span class="sxs-lookup"><span data-stu-id="80fa2-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="80fa2-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="80fa2-113">Scope</span></span>   | <span data-ttu-id="80fa2-114">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="80fa2-114">Transparent</span></span> |
| <span data-ttu-id="80fa2-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="80fa2-115">Version</span></span> | <span data-ttu-id="80fa2-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="80fa2-116">4.7.2</span></span>       |
| <span data-ttu-id="80fa2-117">Tür</span><span class="sxs-lookup"><span data-stu-id="80fa2-117">Type</span></span>    | <span data-ttu-id="80fa2-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="80fa2-118">Retargeting</span></span> |
