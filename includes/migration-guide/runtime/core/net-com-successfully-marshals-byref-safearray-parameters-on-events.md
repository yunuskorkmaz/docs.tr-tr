---
ms.openlocfilehash: 1907c9b82c9685899d328f67da8001c0fa4fb697
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496810"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="d686d-101">.NET COM, olaylardaki ByRef SafeArray parametrelerini başarıyla sıralar</span><span class="sxs-lookup"><span data-stu-id="d686d-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="d686d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d686d-102">Details</span></span>

<span data-ttu-id="d686d-103">.NET Framework 4.7.2 ve önceki sürümlerde, bir COM olayında bir ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parametresi yerel koda geri hazırlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d686d-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="d686d-104">Bu değişiklik ile [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarıyla sıraya sokulur.</span><span class="sxs-lookup"><span data-stu-id="d686d-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="d686d-105">[x] süslenmiş</span><span class="sxs-lookup"><span data-stu-id="d686d-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="d686d-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="d686d-106">Suggestion</span></span>

<span data-ttu-id="d686d-107">ByRef SafeArray parametrelerinin COM olayları üzerinde düzgün şekilde sıralanmasını istiyorsanız, uygulama yapılandırmanıza aşağıdaki yapılandırma anahtarını ekleyerek bu kodu devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d686d-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="d686d-108">Name</span><span class="sxs-lookup"><span data-stu-id="d686d-108">Name</span></span>    | <span data-ttu-id="d686d-109">Değer</span><span class="sxs-lookup"><span data-stu-id="d686d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d686d-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d686d-110">Scope</span></span>   |<span data-ttu-id="d686d-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="d686d-111">Minor</span></span>|
|<span data-ttu-id="d686d-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d686d-112">Version</span></span>|<span data-ttu-id="d686d-113">4,8</span><span class="sxs-lookup"><span data-stu-id="d686d-113">4.8</span></span>|
|<span data-ttu-id="d686d-114">Tür</span><span class="sxs-lookup"><span data-stu-id="d686d-114">Type</span></span>|<span data-ttu-id="d686d-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="d686d-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d686d-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d686d-116">Affected APIs</span></span>

<span data-ttu-id="d686d-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="d686d-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
