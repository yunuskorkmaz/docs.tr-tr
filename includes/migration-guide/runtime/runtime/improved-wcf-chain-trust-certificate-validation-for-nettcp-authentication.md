---
ms.openlocfilehash: f6553444e13416850a398ae5bcb6574f2a69bd2d
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477413"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a><span data-ttu-id="4ec7b-101">Net. TCP sertifikası kimlik doğrulaması için iyileştirilmiş WCF zinciri güven sertifikası doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4ec7b-101">Improved WCF chain trust certificate validation for Net.Tcp certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="4ec7b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4ec7b-102">Details</span></span>

<span data-ttu-id="4ec7b-103">.NET Framework 4.7.2, WCF ile aktarım güvenliği ile sertifika kimlik doğrulaması kullanılırken zincir güven sertifikası doğrulamasını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-103">.NET Framework 4.7.2 improves chain trust certificate validation when using certificate authentication with transport security with WCF.</span></span> <span data-ttu-id="4ec7b-104">Bu gelişle, istemci kimlik doğrulaması için bir sunucuda kimlik doğrulaması yapmak üzere kullanılan istemci sertifikalarının yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-104">With this improvement, client certificates that are used to authenticate to a server must be configured for client authentication.</span></span>  <span data-ttu-id="4ec7b-105">Benzer şekilde sunucu kimlik doğrulaması için olan sunucu sertifikalarının sunucu kimlik doğrulaması için yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-105">Similarly server certificates that are for the authenticating a server must be configured for server authentication.</span></span> <span data-ttu-id="4ec7b-106">Bu değişiklik ile, kök sertifika devre dışıysa, sertifika zinciri doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-106">With this change, if the root certificate is disabled, the certificate chain validation fails.</span></span> <span data-ttu-id="4ec7b-107">Ayrıca, Windows Güvenlik Toplaması aracılığıyla .NET Framework 3,5 ve sonraki sürümlere aynı değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-107">The same change was also made to .NET Framework 3.5 and later versions via Windows security roll-up.</span></span> <span data-ttu-id="4ec7b-108">Daha fazla bilgi için [buradan](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7)daha fazla bilgi edinebilirsiniz. Bu değişiklik varsayılan olarak açıktır ve bir yapılandırma ayarı tarafından kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-108">You can find more information [here](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7).This change is on by default and can be turned off by a configuration setting.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4ec7b-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="4ec7b-109">Suggestion</span></span>

<ul><li><span data-ttu-id="4ec7b-110">Sunucunuzun ve istemci sertifikalarınızın gerekli EKU OID 'ye sahip olup olmadığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-110">Validate if your server and client certification has the required EKU OID.</span></span> <span data-ttu-id="4ec7b-111">Aksi takdirde, sertifikalarınızı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-111">If not, update your certification.</span></span></li><li><span data-ttu-id="4ec7b-112">Kök sertifikanızın geçersiz olup olmadığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-112">Validate if your root certificate is invalid.</span></span> <span data-ttu-id="4ec7b-113">Bu durumda, kök sertifikayı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-113">If so, update the root certificate.</span></span></li><li><span data-ttu-id="4ec7b-114">Değişikliği devre dışı bırakma: sertifikayı Güncelleştirememekle birlikte, aşağıdaki yapılandırma ayarıyla son derece değişikliği geçici olarak çözebilirsiniz, ancak değişikliği devre dışı bıraktığınızda sisteminiz güvenlik sorununa karşı savunmasız kalır.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-114">How to opt out of the change: If you can't update the certificate, you can work around the breaking change temporarily with the following configuration setting,  However, opting out of the change will leave your system vulnerable to the security issue.</span></span></li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="4ec7b-115">Ad</span><span class="sxs-lookup"><span data-stu-id="4ec7b-115">Name</span></span>    | <span data-ttu-id="4ec7b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4ec7b-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4ec7b-117">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4ec7b-117">Scope</span></span>   |<span data-ttu-id="4ec7b-118">İkincil</span><span class="sxs-lookup"><span data-stu-id="4ec7b-118">Minor</span></span>|
|<span data-ttu-id="4ec7b-119">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4ec7b-119">Version</span></span>|<span data-ttu-id="4ec7b-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="4ec7b-120">4.7.2</span></span>|
|<span data-ttu-id="4ec7b-121">Tür</span><span class="sxs-lookup"><span data-stu-id="4ec7b-121">Type</span></span>|<span data-ttu-id="4ec7b-122">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="4ec7b-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4ec7b-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4ec7b-123">Affected APIs</span></span>

<span data-ttu-id="4ec7b-124">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="4ec7b-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
