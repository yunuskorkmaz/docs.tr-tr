---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65199535"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM olayları ByRef SAFEARRAY'i parametreleri başarıyla sürekliliğe devreder

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerinde, ByRef [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) bir COM olay parametresi yerel koda geri sıralamakta başarısız olurdu.  Bu değişikliğe [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarılı bir şekilde sıralanır.<ul><li>[x] quirked</li></ul>|
|Öneri|Düzgün bir şekilde COM olayları parametreleri ByRef SAFEARRAY'i sıralama yürütmeyi keserse, bu kod, uygulamanın yapılandırma için aşağıdaki yapılandırma anahtarı ekleyerek devre dışı bırakabilirsiniz:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Çalışma zamanı|
