---
ms.openlocfilehash: 8aff4b1aa329d6fdfebf3b62e9279e9dfe5de0a4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606209"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>ServicePointManager. SecurityProtocol varsayılan değeri SecurityProtocolType.SysTItem ' dır. Varsayılanını

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ' i hedefleyen uygulamalarla başlayarak, özelliğin varsayılan değeri <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> . Bu değişiklik, SslStream (FTP, HTTPS ve SMTP gibi) tabanlı .NET Framework ağ API 'Lerinin, .NET Framework tarafından tanımlanan sabit kodlu değerler kullanmak yerine işletim sisteminden varsayılan güvenlik protokollerini devralmasını sağlar. Varsayılan, işletim sistemine ve sistem yöneticisi tarafından gerçekleştirilen özel yapılandırmaya göre farklılık gösterir. Windows işletim sisteminin her sürümünde varsayılan SChannel protokolü hakkında daha fazla bilgi için bkz. [TLS/SSL (Schannel SSP) protokolleri](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>.NET Framework önceki bir sürümünü hedefleyen uygulamalar için, özelliğin varsayılan değeri <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> hedeflenen .NET Framework sürümüne bağlıdır. Daha fazla bilgi için [.NET Framework 4.5.2 'ten 4,6 sürümüne geçiş Için yeniden hedefleme değişikliklerinin ağ bölümüne](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) bakın.

#### <a name="suggestion"></a>Öneri

Bu değişiklik .NET Framework 4,7 veya sonraki sürümlerini hedefleyen uygulamaları etkiler. Sistem varsayılanından güvenmek yerine tanımlı bir protokol kullanmayı tercih ediyorsanız, özelliğin değerini açıkça ayarlayabilirsiniz <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> . Bu değişiklik istenmeyen ise, [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümüne bir yapılandırma ayarı ekleyerek bunu devre dışı bırakabilirsiniz. Aşağıdaki örnek hem `<runtime>` bölümünü hem de geri `Switch.System.Net.DontEnableSystemDefaultTlsVersions` çevirme anahtarını gösterir:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSystemDefaultTlsVersions=true" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>
