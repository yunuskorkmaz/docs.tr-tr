---
ms.openlocfilehash: 77e9d28d79a92cf1523e4ef5779d78394b00ae80
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622083"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="43549-101">.NET COM, olaylardaki ByRef SafeArray parametrelerini başarıyla sıralar</span><span class="sxs-lookup"><span data-stu-id="43549-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="43549-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="43549-102">Details</span></span>

<span data-ttu-id="43549-103">.NET Framework 4.7.2 ve önceki sürümlerde, bir COM olayında bir ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parametresi yerel koda geri hazırlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="43549-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="43549-104">Bu değişiklik ile [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarıyla sıraya sokulur.</span><span class="sxs-lookup"><span data-stu-id="43549-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="43549-105">[x] süslenmiş</span><span class="sxs-lookup"><span data-stu-id="43549-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="43549-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="43549-106">Suggestion</span></span>

<span data-ttu-id="43549-107">ByRef SafeArray parametrelerinin COM olayları üzerinde düzgün şekilde sıralanmasını istiyorsanız, uygulama yapılandırmanıza aşağıdaki yapılandırma anahtarını ekleyerek bu kodu devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43549-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="43549-108">Name</span><span class="sxs-lookup"><span data-stu-id="43549-108">Name</span></span>    | <span data-ttu-id="43549-109">Değer</span><span class="sxs-lookup"><span data-stu-id="43549-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="43549-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="43549-110">Scope</span></span>   |<span data-ttu-id="43549-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="43549-111">Minor</span></span>|
|<span data-ttu-id="43549-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="43549-112">Version</span></span>|<span data-ttu-id="43549-113">4,8</span><span class="sxs-lookup"><span data-stu-id="43549-113">4.8</span></span>|
|<span data-ttu-id="43549-114">Tür</span><span class="sxs-lookup"><span data-stu-id="43549-114">Type</span></span>|<span data-ttu-id="43549-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="43549-115">Runtime</span></span>|
