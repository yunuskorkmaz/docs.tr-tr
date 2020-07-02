---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614913"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a><span data-ttu-id="043f0-101">WPF PackageDigitalSignatureManager için varsayılan karma algoritması artık SHA256</span><span class="sxs-lookup"><span data-stu-id="043f0-101">The default hash algorithm for WPF PackageDigitalSignatureManager is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="043f0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="043f0-102">Details</span></span>

<span data-ttu-id="043f0-103">, `System.IO.Packaging.PackageDigitalSignatureManager` WPF paketleriyle ilgili olarak dijital imzalar için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="043f0-103">The `System.IO.Packaging.PackageDigitalSignatureManager` provides functionality for digital signatures in relation to WPF packages.</span></span>  <span data-ttu-id="043f0-104">.NET Framework 4,7 ve önceki sürümlerde, <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType> bir paketin parçalarını imzalamak için kullanılan varsayılan algoritma () SHA1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="043f0-104">In the .NET Framework 4.7 and earlier versions, the default algorithm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) used for signing parts of a package was SHA1.</span></span>  <span data-ttu-id="043f0-105">SHA1 ile ilgili en son güvenlik sorunları nedeniyle, bu varsayılan değer .NET Framework 4.7.1 ile başlayarak SHA256 olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="043f0-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.1.</span></span>  <span data-ttu-id="043f0-106">Bu değişiklik, XPS belgeleri dahil olmak üzere tüm paket imzasını etkiler.</span><span class="sxs-lookup"><span data-stu-id="043f0-106">This change affects all package signing, including XPS documents.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="043f0-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="043f0-107">Suggestion</span></span>

<span data-ttu-id="043f0-108">Bu değişikliği kullanmak isteyen bir geliştirici .NET Framework 4.7.1 veya önceki işlevselliği gerektiren bir geliştirici, .NET Framework 4.7.1 ya da daha fazlasını hedeflemek için aşağıdaki AppContext bayrağını uygun şekilde ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="043f0-108">A developer who wants to utilize this change while targeting a framework version below .NET Framework 4.7.1 or a developer who requires the previous functionality while targeting .NET Framework 4.7.1 or greater can set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="043f0-109">True değeri, varsayılan algoritma olarak SHA1 kullanılmasına neden olur; SHA256 içinde yanlış sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="043f0-109">A value of true will result in SHA1 being used as the default algorithm; false results in SHA256.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="043f0-110">Name</span><span class="sxs-lookup"><span data-stu-id="043f0-110">Name</span></span>    | <span data-ttu-id="043f0-111">Değer</span><span class="sxs-lookup"><span data-stu-id="043f0-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="043f0-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="043f0-112">Scope</span></span>   | <span data-ttu-id="043f0-113">Edge</span><span class="sxs-lookup"><span data-stu-id="043f0-113">Edge</span></span>        |
| <span data-ttu-id="043f0-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="043f0-114">Version</span></span> | <span data-ttu-id="043f0-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="043f0-115">4.7.1</span></span>       |
| <span data-ttu-id="043f0-116">Tür</span><span class="sxs-lookup"><span data-stu-id="043f0-116">Type</span></span>    | <span data-ttu-id="043f0-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="043f0-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="043f0-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="043f0-118">Affected APIs</span></span>

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
