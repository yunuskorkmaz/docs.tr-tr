---
ms.openlocfilehash: d5768a0c25bcd0880cbffde9e57ca9fe7a81cf06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665717"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="14e8d-101">.NET COM olayları ByRef SAFEARRAY'i parametreleri başarıyla sürekliliğe devreder</span><span class="sxs-lookup"><span data-stu-id="14e8d-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="14e8d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="14e8d-102">Details</span></span>|<span data-ttu-id="14e8d-103">.NET Framework 4.7.2 ve önceki sürümlerinde, ByRef [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) bir COM olay parametresi yerel koda geri sıralamakta başarısız olurdu.</span><span class="sxs-lookup"><span data-stu-id="14e8d-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="14e8d-104">Bu değişikliğe [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) başarıyla sıraya şimdi.</span><span class="sxs-lookup"><span data-stu-id="14e8d-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="14e8d-105">[x] quirked</span><span class="sxs-lookup"><span data-stu-id="14e8d-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="14e8d-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="14e8d-106">Suggestion</span></span>|<span data-ttu-id="14e8d-107">COM olayları ByRef SAFEARRAY'i parametreleri doğru şekilde taşıma yürütmeyi keserse, bu kod, uygulamanın yapılandırma için aşağıdaki yapılandırma anahtarı ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="14e8d-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="14e8d-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="14e8d-108">Scope</span></span>|<span data-ttu-id="14e8d-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="14e8d-109">Minor</span></span>|
|<span data-ttu-id="14e8d-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="14e8d-110">Version</span></span>|<span data-ttu-id="14e8d-111">4.8</span><span class="sxs-lookup"><span data-stu-id="14e8d-111">4.8</span></span>|
|<span data-ttu-id="14e8d-112">Tür</span><span class="sxs-lookup"><span data-stu-id="14e8d-112">Type</span></span>|<span data-ttu-id="14e8d-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="14e8d-113">Runtime</span></span>|
