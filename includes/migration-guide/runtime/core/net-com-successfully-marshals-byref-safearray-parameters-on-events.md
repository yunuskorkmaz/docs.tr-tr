---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440290"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM, olaylardaki ByRef SafeArray parametrelerini başarıyla sıralar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerde, bir COM olayında bir ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parametresi yerel koda geri hazırlanmayabilir.  Bu değişiklik ile [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarıyla sıraya sokulur.<ul><li>[x] süslenmiş</li></ul>|
|Öneri|ByRef SafeArray parametrelerinin COM olayları üzerinde düzgün şekilde sıralanmasını istiyorsanız, uygulama yapılandırmanıza aşağıdaki yapılandırma anahtarını ekleyerek bu kodu devre dışı bırakabilirsiniz:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|`Scope`|Küçük|
|Version|4.8|
|Type|Çalışma zamanı|
