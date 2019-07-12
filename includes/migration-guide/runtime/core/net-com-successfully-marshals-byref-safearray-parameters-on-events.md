---
ms.openlocfilehash: 2f4f92c8615b328caee2ad0b90028c76048026f4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802606"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="4f994-101">.NET COM olayları ByRef SAFEARRAY'i parametreleri başarıyla sürekliliğe devreder</span><span class="sxs-lookup"><span data-stu-id="4f994-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4f994-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4f994-102">Details</span></span>|<span data-ttu-id="4f994-103">.NET Framework 4.7.2 ve önceki sürümlerinde, ByRef [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) bir COM olay parametresi yerel koda geri sıralamakta başarısız olurdu.</span><span class="sxs-lookup"><span data-stu-id="4f994-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="4f994-104">Bu değişikliğe [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) başarıyla sıraya şimdi.</span><span class="sxs-lookup"><span data-stu-id="4f994-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="4f994-105">[x] quirked</span><span class="sxs-lookup"><span data-stu-id="4f994-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="4f994-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="4f994-106">Suggestion</span></span>|<span data-ttu-id="4f994-107">COM olayları ByRef SAFEARRAY'i parametreleri doğru şekilde taşıma yürütmeyi keserse, bu kod, uygulamanın yapılandırma için aşağıdaki yapılandırma anahtarı ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4f994-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="4f994-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4f994-108">Scope</span></span>|<span data-ttu-id="4f994-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="4f994-109">Minor</span></span>|
|<span data-ttu-id="4f994-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4f994-110">Version</span></span>|<span data-ttu-id="4f994-111">4.8</span><span class="sxs-lookup"><span data-stu-id="4f994-111">4.8</span></span>|
|<span data-ttu-id="4f994-112">Tür</span><span class="sxs-lookup"><span data-stu-id="4f994-112">Type</span></span>|<span data-ttu-id="4f994-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="4f994-113">Runtime</span></span>|

