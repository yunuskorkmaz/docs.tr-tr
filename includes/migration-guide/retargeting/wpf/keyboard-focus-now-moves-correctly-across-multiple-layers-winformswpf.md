---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614941"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a><span data-ttu-id="d6964-101">Klavye odağı artık birden çok WinForms/WPF barındırma katmanında doğru şekilde taşınıyor</span><span class="sxs-lookup"><span data-stu-id="d6964-101">Keyboard focus now moves correctly across multiple layers of WinForms/WPF hosting</span></span>

#### <a name="details"></a><span data-ttu-id="d6964-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d6964-102">Details</span></span>

<span data-ttu-id="d6964-103">Bir WinForms denetimini barındıran bir WPF uygulamasını, WPF denetimlerini barındıran bir şekilde düşünün.</span><span class="sxs-lookup"><span data-stu-id="d6964-103">Consider a WPF application hosting a WinForms control which in turn hosts WPF controls.</span></span> <span data-ttu-id="d6964-104">Bu katmandaki ilk veya son denetim WPF ise, kullanıcılar WinForms katmanının dışına sekme yapamaz `System.Windows.Forms.Integration.ElementHost` .</span><span class="sxs-lookup"><span data-stu-id="d6964-104">Users may not be able to tab out of the WinForms layer if the first or last control in that layer is the WPF `System.Windows.Forms.Integration.ElementHost`.</span></span> <span data-ttu-id="d6964-105">Bu değişiklik bu sorunu düzeltir ve kullanıcılar artık WinForms katmanının dışına sekme verebilir. Odaklanmayı kullanan otomatikleştirilmiş uygulamalar, WinForms katmanını hiçbir şekilde yok etmeme, artık beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d6964-105">This change fixes this issue, and users are now able to tab out of the WinForms layer.Automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d6964-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="d6964-106">Suggestion</span></span>

<span data-ttu-id="d6964-107">.NET 4.7.2 'in altında bir Framework sürümünü hedeflerken bu değişikliği kullanmak isteyen bir geliştirici, değişikliğin etkinleştirilmesi için aşağıdaki AppContext bayrakları kümesini false olarak ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d6964-107">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 can set the following set of AppContext flags to false for the change to be enabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="d6964-108">Daha sonraki geliştirmeleri almak için WPF uygulamalarının tüm erken erişilebilirlik geliştirmelerini kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="d6964-108">WPF applications must opt in to all early accessibility improvements to get the later improvements.</span></span> <span data-ttu-id="d6964-109">Diğer bir deyişle, ve anahtarlarının her ikisi de, `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2` .NET 4.7.2 veya üzerini hedeflerken önceki Işlevselliği gerektiren Seta geliştiricisi olmalıdır değişikliğin devre dışı bırakılması Için aşağıdaki AppContext bayrağını True olarak ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d6964-109">In other words, both the `Switch.UseLegacyAccessibilityFeatures` and the `Switch.UseLegacyAccessibilityFeatures.2` switches must be setA developer who requires the previous functionality while targeting .NET 4.7.2 or greater can set the following AppContext flag to true for the change to be disabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="d6964-110">Name</span><span class="sxs-lookup"><span data-stu-id="d6964-110">Name</span></span>    | <span data-ttu-id="d6964-111">Değer</span><span class="sxs-lookup"><span data-stu-id="d6964-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d6964-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d6964-112">Scope</span></span>   | <span data-ttu-id="d6964-113">Edge</span><span class="sxs-lookup"><span data-stu-id="d6964-113">Edge</span></span>        |
| <span data-ttu-id="d6964-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d6964-114">Version</span></span> | <span data-ttu-id="d6964-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="d6964-115">4.7.2</span></span>       |
| <span data-ttu-id="d6964-116">Tür</span><span class="sxs-lookup"><span data-stu-id="d6964-116">Type</span></span>    | <span data-ttu-id="d6964-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="d6964-117">Retargeting</span></span> |
