---
ms.openlocfilehash: aadf5eb85c8736c29639d49bc8baf21545d2467c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606789"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="fa61e-101">.NET COM, olaylardaki ByRef SafeArray parametrelerini başarıyla sıralar</span><span class="sxs-lookup"><span data-stu-id="fa61e-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="fa61e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fa61e-102">Details</span></span>

<span data-ttu-id="fa61e-103">.NET Framework 4.7.2 ve önceki sürümlerde, bir COM olayında bir ByRef [SAFEARRAY](/windows/desktop/api/oaidl/ns-oaidl-safearray) parametresi yerel koda geri hazırlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fa61e-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="fa61e-104">Bu değişiklik ile [SAFEARRAY](/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarıyla sıraya sokulur.</span><span class="sxs-lookup"><span data-stu-id="fa61e-104">With this change the [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="fa61e-105">[x] süslenmiş</span><span class="sxs-lookup"><span data-stu-id="fa61e-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="fa61e-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="fa61e-106">Suggestion</span></span>

<span data-ttu-id="fa61e-107">ByRef SafeArray parametrelerinin COM olayları üzerinde düzgün şekilde sıralanmasını istiyorsanız, uygulama yapılandırmanıza aşağıdaki yapılandırma anahtarını ekleyerek bu kodu devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fa61e-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="fa61e-108">Name</span><span class="sxs-lookup"><span data-stu-id="fa61e-108">Name</span></span>    | <span data-ttu-id="fa61e-109">Değer</span><span class="sxs-lookup"><span data-stu-id="fa61e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fa61e-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fa61e-110">Scope</span></span>   |<span data-ttu-id="fa61e-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="fa61e-111">Minor</span></span>|
|<span data-ttu-id="fa61e-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fa61e-112">Version</span></span>|<span data-ttu-id="fa61e-113">4,8</span><span class="sxs-lookup"><span data-stu-id="fa61e-113">4.8</span></span>|
|<span data-ttu-id="fa61e-114">Tür</span><span class="sxs-lookup"><span data-stu-id="fa61e-114">Type</span></span>|<span data-ttu-id="fa61e-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="fa61e-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fa61e-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fa61e-116">Affected APIs</span></span>

<span data-ttu-id="fa61e-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="fa61e-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
