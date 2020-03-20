---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68440290"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="d191c-101">.NET COM, ByRef SafeArray parametrelerini etkinliklerle ilgili başarıyla</span><span class="sxs-lookup"><span data-stu-id="d191c-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d191c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d191c-102">Details</span></span>|<span data-ttu-id="d191c-103">.NET Framework 4.7.2 ve önceki sürümlerinde, bir COM olayındaki ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parametresi yerel koda geri döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="d191c-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="d191c-104">Bu değişiklikle [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarıyla düzenesi sağlanmış oldu.</span><span class="sxs-lookup"><span data-stu-id="d191c-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="d191c-105">[ x ] Tuhaf</span><span class="sxs-lookup"><span data-stu-id="d191c-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="d191c-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="d191c-106">Suggestion</span></span>|<span data-ttu-id="d191c-107">Com Events'te ByRef SafeArray parametrelerini düzgün bir şekilde sıralıyorsa, uygulama konfiginize aşağıdaki yapılandırma anahtarını ekleyerek bu kodu devre dışı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d191c-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="d191c-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d191c-108">Scope</span></span>|<span data-ttu-id="d191c-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="d191c-109">Minor</span></span>|
|<span data-ttu-id="d191c-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d191c-110">Version</span></span>|<span data-ttu-id="d191c-111">4.8</span><span class="sxs-lookup"><span data-stu-id="d191c-111">4.8</span></span>|
|<span data-ttu-id="d191c-112">Tür</span><span class="sxs-lookup"><span data-stu-id="d191c-112">Type</span></span>|<span data-ttu-id="d191c-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="d191c-113">Runtime</span></span>|
