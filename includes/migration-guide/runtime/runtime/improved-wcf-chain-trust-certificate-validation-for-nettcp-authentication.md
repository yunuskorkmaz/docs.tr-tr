---
ms.openlocfilehash: e69ed64390504af872fa6785aa0b7d6c4db84ef0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "69671040"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Net.Tcp sertifikası kimlik doğrulaması için geliştirilmiş WCF zincir güven sertifikası doğrulaması

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2, WCF ile taşıma güvenliği ile sertifika kimlik doğrulaması kullanırken zincir güven sertifikası doğrulamasını geliştirir. Bu geliştirmeyle, bir sunucuya kimlik doğrulaması yapmak için kullanılan istemci sertifikalarının istemci kimlik doğrulaması için yapılandırılması gerekir.  Benzer şekilde, bir sunucunun kimlik doğrulaması için olan sunucu sertifikaları sunucu kimlik doğrulaması için yapılandırılmalıdır. Bu değişiklikle, kök sertifika devre dışı bırakılırsa, sertifika zinciri doğrulaması başarısız olur. Aynı değişiklik ,NET Framework 3.5 ve sonraki sürümler için Windows güvenlik roll-up üzerinden yapıldı. [Burada](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7)daha fazla bilgi bulabilirsiniz. Bu değişiklik varsayılan olarak açıktır ve bir yapılandırma ayarı tarafından kapatılabilir.|
|Öneri|<ul><li>Sunucunuz ve istemci sertifikanız gerekli EKU OID'ye sahipse doğrulayın. Değilse, sertifikanızı güncelleştirin.</li><li>Kök sertifikanız geçersizse doğrulayın. Öyleyse, kök sertifikayı güncelleştirin.</li><li>Değişikliği nasıl devre dışı bırakabilirsiniz: Sertifikayı güncelleştiremezseniz, kesme değişikliğini geçici olarak aşağıdaki configration ayarı ile çözebilirsiniz, Ancak, değişikliği devre dışı bırakmak sisteminizi güvenlik sorununa karşı savunmasız bırakır.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.2|
|Tür|Çalışma Zamanı|
