---
ms.openlocfilehash: d5768a0c25bcd0880cbffde9e57ca9fe7a81cf06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982279"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM olayları ByRef SAFEARRAY'i parametreleri başarıyla sürekliliğe devreder

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerinde, ByRef [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) bir COM olay parametresi yerel koda geri sıralamakta başarısız olurdu.  Bu değişikliğe [SAFEARRAY'i](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) başarıyla sıraya şimdi.<ul><li>[x] quirked</li></ul>|
|Öneri|COM olayları ByRef SAFEARRAY'i parametreleri doğru şekilde taşıma yürütmeyi keserse, bu kod, uygulamanın yapılandırma için aşağıdaki yapılandırma anahtarı ekleyerek devre dışı bırakabilirsiniz:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Çalışma zamanı|
