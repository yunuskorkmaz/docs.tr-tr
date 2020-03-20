---
ms.openlocfilehash: 122a5ab3e2def7c19d3d523881fcb15df4dbca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235555"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>ServicePointManager.SecurityProtocol varsayılan değeri SecurityProtocolType.System.Default olduğunu

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7'yi hedefleyen uygulamalardan başlayarak, <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>özelliğin varsayılan değeri . Bu değişiklik, .NET Framework tarafından tanımlanan sabit kodlu değerleri kullanmak yerine varsayılan güvenlik protokollerini işletim sisteminden devralmak yerine SslStream'e (FTP, HTTPS ve SMTP gibi) dayalı .NET Framework ağ API'lerinin devralınmasına olanak tanır. Varsayılan, işletim sistemine ve sistem yöneticisi tarafından gerçekleştirilen özel yapılandırmaya göre değişir. Windows işletim sisteminin her sürümündeki varsayılan SChannel protokolü hakkında bilgi için [TLS/SSL (Schannel SSP) protokollerine](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-)bakın.</p>.NET Framework'ün önceki bir sürümünü hedefleyen uygulamalarda, <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliğin varsayılan değeri hedeflenen .NET Framework sürümüne bağlıdır. Daha fazla bilgi [için .NET Framework 4.5.2'den 4.6'ya geçiş için Yeniden Hedefleme Değişikliklerinin Ağ bölümüne](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) bakın.|
|Öneri|Bu değişiklik,.NET Framework 4.7 veya sonraki sürümlerihedefleyen uygulamaları etkiler. <br>Sistem varsayılanına güvenmek yerine tanımlı bir iletişim kuralı kullanmayı tercih ederseniz, <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliğin değerini açıkça ayarlayabilirsiniz.<br>Bu değişiklik istenmiyorsa, uygulama yapılandırma dosyanızın [ \<çalışma zamanı>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne bir yapılandırma ayarı ekleyerek bu değişikliği devre dışı kullanabilirsiniz. Aşağıdaki örnekte hem <code>&lt;runtime&gt;</code> bölüm <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> hem de devre dışı bırakma anahtarı gösterilmektedir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|
