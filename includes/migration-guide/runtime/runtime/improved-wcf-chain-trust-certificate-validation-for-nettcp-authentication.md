---
ms.openlocfilehash: 4a0f866bc11a06ea6fcd4ab3a8320bbb6ffa5d91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621376"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Net. TCP sertifikası kimlik doğrulaması için iyileştirilmiş WCF zinciri güven sertifikası doğrulaması

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2, WCF ile aktarım güvenliği ile sertifika kimlik doğrulaması kullanılırken zincir güven sertifikası doğrulamasını geliştirir. Bu gelişle, istemci kimlik doğrulaması için bir sunucuda kimlik doğrulaması yapmak üzere kullanılan istemci sertifikalarının yapılandırılması gerekir.  Benzer şekilde sunucu kimlik doğrulaması için olan sunucu sertifikalarının sunucu kimlik doğrulaması için yapılandırılması gerekir. Bu değişiklik ile, kök sertifika devre dışıysa, sertifika zinciri doğrulaması başarısız olur. Ayrıca, Windows Güvenlik Toplaması aracılığıyla .NET Framework 3,5 ve sonraki sürümlere aynı değişiklik yapılmıştır. Daha fazla bilgi için [buradan](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7)daha fazla bilgi edinebilirsiniz. Bu değişiklik varsayılan olarak açıktır ve bir yapılandırma ayarı tarafından kapatılabilir.

#### <a name="suggestion"></a>Öneri

<ul><li>Sunucunuzun ve istemci sertifikalarınızın gerekli EKU OID 'ye sahip olup olmadığını doğrulayın. Aksi takdirde, sertifikalarınızı güncelleştirin.</li><li>Kök sertifikanızın geçersiz olup olmadığını doğrulayın. Bu durumda, kök sertifikayı güncelleştirin.</li><li>Değişikliği devre dışı bırakma: sertifikayı güncelleştirememekle birlikte, aşağıdaki yapılandırma ayarıyla geçici değişikliği geçici olarak çözebilirsiniz, ancak değişikliği devre dışı bıraktığınızda sisteminiz güvenlik sorununa karşı savunmasız bırakılır.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.7.2|
|Tür|Çalışma Zamanı|
