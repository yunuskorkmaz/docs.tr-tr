---
ms.openlocfilehash: 2359dafb9042c13ae75e644d4ea655f53c14e95e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804374"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>TransportWithMessageCredential güvenlik modu ile WCF bağlama

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1'den başlayarak, TransportWithMessageCredential güvenlik modunu kullanan WCF bağlama, &quot;asimetrik güvenlik anahtarları için üstbilgilere&quot; imzasız iletiler alacak şekilde ayarlanabilir. Varsayılan olarak, &quot;üstbilgi için&quot; imzalanmamış .NET Framework 4.6.1'de reddedilmeye devam eder. Yalnızca switch.System.ServiceModel.AllowUnsignedToHeader yapılandırma anahtarını kullanarak bir uygulama bu yeni çalışma moduna geçerse kabul edilir.|
|Öneri|Bu bir kabul özelliği olduğundan, varolan uygulamaların davranışını etkilememelidir.<br/>Yeni davranışın kullanılıp kullanılmadığını denetlemek için aşağıdaki yapılandırma ayarını kullanın:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|
