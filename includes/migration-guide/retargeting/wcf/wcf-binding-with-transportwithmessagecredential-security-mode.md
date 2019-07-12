---
ms.openlocfilehash: ce7e2db3f74ec24f47b1c224335451c997c4c349
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804374"
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

