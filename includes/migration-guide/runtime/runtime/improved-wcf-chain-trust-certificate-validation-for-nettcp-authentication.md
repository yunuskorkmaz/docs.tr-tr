---
ms.openlocfilehash: 05116d80fcd6b75f366a2542ad2eadd5f434991c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805269"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Geliştirilmiş WCF zinciri güven sertifikası doğrulama Net.Tcp sertifika kimlik doğrulaması

|   |   |
|---|---|
|Ayrıntılar|.NET framework 4.7.2 zinciri güven sertifikası doğrulama sertifikası kimlik doğrulamasını WCF ile Aktarım güvenliği ile kullanırken artırır. Bu geliştirmeyle, istemci sertifikaları için bir sunucu kimliğini doğrulaması için kullanılan istemci kimlik doğrulaması için yapılandırılmış olması gerekir.  Benzer şekilde, bir sunucu kimlik doğrulaması için sertifikaları sunucu kimlik doğrulaması için yapılandırılmış olması gerekir. Kök sertifikayı devre dışı bırakılırsa, bu değişiklik, sertifika zinciri doğrulaması başarısız olur. Aynı değişikliği de .NET Framework 3.5 ve sonraki sürümler ile Windows Güvenlik dökümü yapıldı. Daha fazla bilgi bulabilirsiniz [burada](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Bu değişiklik, varsayılan olarak açıktır ve bir yapılandırma ayarı tarafından devre dışı bırakılabilir.|
|Öneri|<ul><li>Gerekli EKU OID'sini sunucu ve istemci sertifikanız varsa, doğrulayın. Değilse, sertifikanızı güncelleştirin.</li><li>Kök sertifikanızın geçersizse doğrulayın. Bu durumda, kök sertifikayı güncelleştirin.</li><li>Değişikliğin dışında nasıl: Sertifika güncelleştirilemiyor, geçici olarak bozucu değişikliğin şu yapılandırma ayarı ile çalışabilir, ancak dışında değişikliği kabul edilirse sisteminizi güvenlik sorunu karşı savunmasız bırakır.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.2|
|Tür|Çalışma zamanı|
