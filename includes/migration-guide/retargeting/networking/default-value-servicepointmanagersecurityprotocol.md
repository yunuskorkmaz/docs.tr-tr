---
ms.openlocfilehash: 7b86365e841defb78558b10fa171a88031b4820e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859175"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Varsayılan ServicePointManager.SecurityProtocol SecurityProtocolType.System.Default değeri

|   |   |
|---|---|
|Ayrıntılar|Varsayılan değer olan .NET Framework 4.7 hedefleyen uygulamaları ile başlayan <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliği <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Bu değişiklik, .NET Framework ağ API'leri SslStream (örneğin, FTP, HTTPS ve SMTP) .NET Framework tarafından tanımlanan sabit kodlanmış değerler yerine bu işletim sistemindeki varsayılan güvenlik protokollerini devralmak için temel sağlar. Varsayılan işletim sistemi ve Sistem Yöneticisi tarafından gerçekleştirilen tüm özel yapılandırma göre değişir. Her bir sürümde Windows işletim sisteminin varsayılan SChannel protokolü hakkında daha fazla bilgi için bkz: [protokolleri de TLS/SSL'deki (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>Varsayılan değer olan .NET Framework'ün önceki bir sürümünü hedefleyen uygulamalar için <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliği hedeflenen .NET Framework sürümüne bağlıdır. Bkz: [yeniden hedefleme değişiklikleri .NET Framework 4.5.2 için 4.6 geçiş için ağ bölümünü](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) daha fazla bilgi için.|
|Öneri|Bu değişiklik, .NET Framework 4.7 veya sonraki sürümlerini hedefleyen uygulamaları etkiler. </br>Tanımlanan bir protokolü kullanmayı tercih yerine, bağlı olan sistem varsayılan değeri açıkça ayarlayabilirsiniz <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliği.</br>Bu değişiklik, istenmeyen ise, dışında bir yapılandırma ayarı ekleyerek seçebilirsiniz [ <runtime> ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma dosyasının. Aşağıdaki örnek her ikisini de gösteren <code>&lt;runtime&gt;</code> bölümü ve <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> çevirme anahtarı:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|`Scope`|Küçük|
|Version|4.7|
|Type|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|

