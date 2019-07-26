---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440290"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="6ca04-101">.NET COM, olaylardaki ByRef SafeArray parametrelerini başarıyla sıralar</span><span class="sxs-lookup"><span data-stu-id="6ca04-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6ca04-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6ca04-102">Details</span></span>|<span data-ttu-id="6ca04-103">.NET Framework 4.7.2 ve önceki sürümlerde, bir COM olayında bir ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parametresi yerel koda geri hazırlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6ca04-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="6ca04-104">Bu değişiklik ile [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarıyla sıraya sokulur.</span><span class="sxs-lookup"><span data-stu-id="6ca04-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="6ca04-105">[x] süslenmiş</span><span class="sxs-lookup"><span data-stu-id="6ca04-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="6ca04-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="6ca04-106">Suggestion</span></span>|<span data-ttu-id="6ca04-107">ByRef SafeArray parametrelerinin COM olayları üzerinde düzgün şekilde sıralanmasını istiyorsanız, uygulama yapılandırmanıza aşağıdaki yapılandırma anahtarını ekleyerek bu kodu devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ca04-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="6ca04-108">`Scope`</span><span class="sxs-lookup"><span data-stu-id="6ca04-108">Scope</span></span>|<span data-ttu-id="6ca04-109">Küçük</span><span class="sxs-lookup"><span data-stu-id="6ca04-109">Minor</span></span>|
|<span data-ttu-id="6ca04-110">Version</span><span class="sxs-lookup"><span data-stu-id="6ca04-110">Version</span></span>|<span data-ttu-id="6ca04-111">4.8</span><span class="sxs-lookup"><span data-stu-id="6ca04-111">4.8</span></span>|
|<span data-ttu-id="6ca04-112">Type</span><span class="sxs-lookup"><span data-stu-id="6ca04-112">Type</span></span>|<span data-ttu-id="6ca04-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="6ca04-113">Runtime</span></span>|
