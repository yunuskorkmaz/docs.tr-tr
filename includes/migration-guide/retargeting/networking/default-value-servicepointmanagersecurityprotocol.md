---
ms.openlocfilehash: de246d78ac319f9da29d5a4aaf65d71deaa4cafb
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760345"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Varsayılan ServicePointManager.SecurityProtocol SecurityProtocolType.System.Default değeri

|   |   |
|---|---|
|Ayrıntılar|Varsayılan değer olan .NET Framework 4.7 hedefleyen uygulamaları ile başlayan <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliği <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Bu değişiklik, .NET Framework ağ API'leri SslStream (örneğin, FTP, HTTPS ve SMTP) .NET Framework tarafından tanımlanan sabit kodlanmış değerler yerine bu işletim sistemindeki varsayılan güvenlik protokollerini devralmak için temel sağlar. Varsayılan işletim sistemi ve Sistem Yöneticisi tarafından gerçekleştirilen tüm özel yapılandırma göre değişir. Her bir sürümde Windows işletim sisteminin varsayılan SChannel protokolü hakkında daha fazla bilgi için bkz: [protokolleri de TLS/SSL'deki (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>Varsayılan değer olan .NET Framework'ün önceki bir sürümünü hedefleyen uygulamalar için <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliği hedeflenen .NET Framework sürümüne bağlıdır. Bkz: [yeniden hedefleme değişiklikleri .NET Framework 4.5.2 için 4.6 geçiş için ağ bölümünü](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) daha fazla bilgi için.|
|Öneri|Bu değişiklik, .NET Framework 4.7 veya sonraki sürümlerini hedefleyen uygulamaları etkiler. <br>Tanımlanan bir protokolü kullanmayı tercih yerine, bağlı olan sistem varsayılan değeri açıkça ayarlayabilirsiniz <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliği.<br>Bu değişiklik, istenmeyen ise, dışında bir yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma dosyasının. Aşağıdaki örnek her ikisini de gösteren <code>&lt;runtime&gt;</code> bölümü ve <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> çevirme anahtarı:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|

