---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65199535"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="f5df4-101">.NET COM olayları ByRef SAFEARRAY'i parametreleri başarıyla sürekliliğe devreder</span><span class="sxs-lookup"><span data-stu-id="f5df4-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f5df4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f5df4-102">Details</span></span>|<span data-ttu-id="f5df4-103">.NET Framework 4.7.2 ve önceki sürümlerinde, ByRef [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) bir COM olay parametresi yerel koda geri sıralamakta başarısız olurdu.</span><span class="sxs-lookup"><span data-stu-id="f5df4-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="f5df4-104">Bu değişikliğe [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarılı bir şekilde sıralanır.</span><span class="sxs-lookup"><span data-stu-id="f5df4-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshaled successfully.</span></span><ul><li><span data-ttu-id="f5df4-105">[x] quirked</span><span class="sxs-lookup"><span data-stu-id="f5df4-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="f5df4-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="f5df4-106">Suggestion</span></span>|<span data-ttu-id="f5df4-107">Düzgün bir şekilde COM olayları parametreleri ByRef SAFEARRAY'i sıralama yürütmeyi keserse, bu kod, uygulamanın yapılandırma için aşağıdaki yapılandırma anahtarı ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5df4-107">If properly marshaling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="f5df4-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f5df4-108">Scope</span></span>|<span data-ttu-id="f5df4-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="f5df4-109">Minor</span></span>|
|<span data-ttu-id="f5df4-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f5df4-110">Version</span></span>|<span data-ttu-id="f5df4-111">4.8</span><span class="sxs-lookup"><span data-stu-id="f5df4-111">4.8</span></span>|
|<span data-ttu-id="f5df4-112">Tür</span><span class="sxs-lookup"><span data-stu-id="f5df4-112">Type</span></span>|<span data-ttu-id="f5df4-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="f5df4-113">Runtime</span></span>|
