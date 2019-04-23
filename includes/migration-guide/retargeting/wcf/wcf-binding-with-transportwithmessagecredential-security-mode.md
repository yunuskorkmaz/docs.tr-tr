---
ms.openlocfilehash: 2359dafb9042c13ae75e644d4ea655f53c14e95e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805288"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>WCF bağlamayla TransportWithMessageCredential güvenlik modu

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1 başlayarak, TransportWithMessageCredential güvenlik modu kullanan WCF bağlaması ile imzalanmamış iletileri alacak şekilde ayarlanabilir &quot;için&quot; asimetrik güvenlik anahtarları için üstbilgiler. Varsayılan olarak, imzasız &quot;için&quot; üst bilgiler .NET Framework 4.6.1 reddedilmesi devam eder. Bir uygulamanın bu yeni Switch.System.ServiceModel.AllowUnsignedToHeader yapılandırma anahtarı kullanarak işlem moduna kabul eder. Bunlar yalnızca kabul edilecektir.|
|Öneri|Bu katılımı özelliği olduğundan, mevcut uygulamaları davranışını etkilenmemelidir.<br/>Yeni davranış veya kullanılıp kullanılmadığını kontrol etmek için şu yapılandırma ayarı kullanın:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|
