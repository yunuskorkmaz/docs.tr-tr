---
ms.openlocfilehash: 207dba9327cfd6debd15c5573697f8950b6c2c95
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86218229"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1. x varsayılan olarak SCH_SEND_AUX_RECORD bayrağını temel SCHANNEL API 'sine geçirir

#### <a name="details"></a>Ayrıntılar

TLS 1. x kullanırken, .NET Framework temeldeki Windows SCHANNEL API 'sine dayanır. .NET Framework 4,6 ' den itibaren [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) bayrağı varsayılan olarak SChannel ' a geçirilir. Bu, SCHANNEL 'ın verileri iki ayrı kayıt halinde, ilki tek bir bayt ve ikinciden <em>n</em>-1 bayt olarak şifrelemesine neden olur. Nadir durumlarda, bu durum istemciler ve mevcut sunucular arasındaki iletişimi, verilerin tek bir kayıtta bulunduğu varsayımını yapan bir şekilde keser.

#### <a name="suggestion"></a>Öneri

Bu değişiklik mevcut bir sunucuyla iletişimi kopararsa, [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümündeki öğesine aşağıdaki anahtarı ekleyerek SCH_SEND_AUX_RECORD bayrağını göndermeyi devre dışı bırakabilir ve verileri ayrı kayıtlara bölmemek için önceki davranışı geri yükleyebilirsiniz:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Aksi takdirde kullanılması önerilmez.

| Ad    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6         |
| Type    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
