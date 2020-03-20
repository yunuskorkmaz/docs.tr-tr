---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68440290"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM, ByRef SafeArray parametrelerini etkinliklerle ilgili başarıyla

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerinde, bir COM olayındaki ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parametresi yerel koda geri döndürülmez.  Bu değişiklikle [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) artık başarıyla düzenesi sağlanmış oldu.<ul><li>[ x ] Tuhaf</li></ul>|
|Öneri|Com Events'te ByRef SafeArray parametrelerini düzgün bir şekilde sıralıyorsa, uygulama konfiginize aşağıdaki yapılandırma anahtarını ekleyerek bu kodu devre dışı kullanabilirsiniz:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Çalışma Zamanı|
