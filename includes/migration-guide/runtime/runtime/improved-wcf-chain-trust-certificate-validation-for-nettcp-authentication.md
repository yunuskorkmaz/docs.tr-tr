---
ms.openlocfilehash: c8f017084fc1ec1eca636ef0178a40559e15b2c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496508"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a><span data-ttu-id="c2c8f-101">Net. TCP sertifikası kimlik doğrulaması için iyileştirilmiş WCF zinciri güven sertifikası doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c2c8f-101">Improved WCF chain trust certificate validation for Net.Tcp certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="c2c8f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c2c8f-102">Details</span></span>

<span data-ttu-id="c2c8f-103">.NET Framework 4.7.2, WCF ile aktarım güvenliği ile sertifika kimlik doğrulaması kullanılırken zincir güven sertifikası doğrulamasını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-103">.NET Framework 4.7.2 improves chain trust certificate validation when using certificate authentication with transport security with WCF.</span></span> <span data-ttu-id="c2c8f-104">Bu gelişle, istemci kimlik doğrulaması için bir sunucuda kimlik doğrulaması yapmak üzere kullanılan istemci sertifikalarının yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-104">With this improvement, client certificates that are used to authenticate to a server must be configured for client authentication.</span></span>  <span data-ttu-id="c2c8f-105">Benzer şekilde sunucu kimlik doğrulaması için olan sunucu sertifikalarının sunucu kimlik doğrulaması için yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-105">Similarly server certificates that are for the authenticating a server must be configured for server authentication.</span></span> <span data-ttu-id="c2c8f-106">Bu değişiklik ile, kök sertifika devre dışıysa, sertifika zinciri doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-106">With this change, if the root certificate is disabled, the certificate chain validation fails.</span></span> <span data-ttu-id="c2c8f-107">Ayrıca, Windows Güvenlik Toplaması aracılığıyla .NET Framework 3,5 ve sonraki sürümlere aynı değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-107">The same change was also made to .NET Framework 3.5 and later versions via Windows security roll-up.</span></span> <span data-ttu-id="c2c8f-108">Daha fazla bilgi için [buradan](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7)daha fazla bilgi edinebilirsiniz. Bu değişiklik varsayılan olarak açıktır ve bir yapılandırma ayarı tarafından kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-108">You can find more information [here](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7).This change is on by default and can be turned off by a configuration setting.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c2c8f-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="c2c8f-109">Suggestion</span></span>

<ul><li><span data-ttu-id="c2c8f-110">Sunucunuzun ve istemci sertifikalarınızın gerekli EKU OID 'ye sahip olup olmadığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-110">Validate if your server and client certification has the required EKU OID.</span></span> <span data-ttu-id="c2c8f-111">Aksi takdirde, sertifikalarınızı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-111">If not, update your certification.</span></span></li><li><span data-ttu-id="c2c8f-112">Kök sertifikanızın geçersiz olup olmadığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-112">Validate if your root certificate is invalid.</span></span> <span data-ttu-id="c2c8f-113">Bu durumda, kök sertifikayı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-113">If so, update the root certificate.</span></span></li><li><span data-ttu-id="c2c8f-114">Değişikliği devre dışı bırakma: sertifikayı güncelleştirememekle birlikte, aşağıdaki yapılandırma ayarıyla geçici değişikliği geçici olarak çözebilirsiniz, ancak değişikliği devre dışı bıraktığınızda sisteminiz güvenlik sorununa karşı savunmasız bırakılır.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-114">How to opt out of the change: If you can't update the certificate, you can work around the breaking change temporarily with the following configration setting,  However, opting out of the change will leave your system vulnerable to the security issue.</span></span></li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c2c8f-115">Name</span><span class="sxs-lookup"><span data-stu-id="c2c8f-115">Name</span></span>    | <span data-ttu-id="c2c8f-116">Değer</span><span class="sxs-lookup"><span data-stu-id="c2c8f-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c2c8f-117">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c2c8f-117">Scope</span></span>   |<span data-ttu-id="c2c8f-118">İkincil</span><span class="sxs-lookup"><span data-stu-id="c2c8f-118">Minor</span></span>|
|<span data-ttu-id="c2c8f-119">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c2c8f-119">Version</span></span>|<span data-ttu-id="c2c8f-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="c2c8f-120">4.7.2</span></span>|
|<span data-ttu-id="c2c8f-121">Tür</span><span class="sxs-lookup"><span data-stu-id="c2c8f-121">Type</span></span>|<span data-ttu-id="c2c8f-122">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="c2c8f-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c2c8f-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c2c8f-123">Affected APIs</span></span>

<span data-ttu-id="c2c8f-124">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="c2c8f-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
