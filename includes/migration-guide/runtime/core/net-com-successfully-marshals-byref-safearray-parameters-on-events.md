---
ms.openlocfilehash: aadf5eb85c8736c29639d49bc8baf21545d2467c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606789"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM, olaylardaki ByRef SafeArray parametrelerini başarıyla sıralar

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2 ve önceki sürümlerde, bir COM olayında bir ByRef [SAFEARRAY](/windows/desktop/api/oaidl/ns-oaidl-safearray) parametresi yerel koda geri hazırlanmayabilir.  Bu değişiklik ile [SAFEARRAY](/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarıyla sıraya sokulur.<ul><li>[x] süslenmiş</li></ul>

#### <a name="suggestion"></a>Öneri

ByRef SafeArray parametrelerinin COM olayları üzerinde düzgün şekilde sıralanmasını istiyorsanız, uygulama yapılandırmanıza aşağıdaki yapılandırma anahtarını ekleyerek bu kodu devre dışı bırakabilirsiniz:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,8|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
