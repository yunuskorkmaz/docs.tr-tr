---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614762"
---
### <a name="sslstream-supports-tls-alerts"></a>SslStream TLS uyarılarını destekler

#### <a name="details"></a>Ayrıntılar

Başarısız bir TLS anlaşması sonrasında, <xref:System.IO.IOException?displayProperty=fullName> <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> ilk g/ç okuma/yazma işlemi tarafından iç özel durum içeren bir iç özel durum oluşturulur. <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName>İçin kodu, <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> [TLS ve SSL uyarıları için Schannel hata kodları](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts)kullanılarak uzak tarafın TLS uyarısıyla eşleştirilebilir. Daha fazla bilgi için bkz. [RFC 2246: Bölüm 7.2.2 hata uyarıları](https://tools.ietf.org/html/rfc2246#section-7.2.2). <br/>.NET Framework 4.6.2 ve önceki sürümlerde, taşıma kanalının (genellikle TCP bağlantısı) yazma veya okuma sırasında, diğer tarafın el sıkışması başarısız olması ve bağlantıyı reddetmesi sırasında zaman aşımına uğrayacağı bir davranıştır.

#### <a name="suggestion"></a>Öneri

Veya gibi ağ g/ç API 'lerini çağıran uygulamalar, <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> <xref:System.IO.IOException> veya <xref:System.TimeoutException?displayProperty=fullName> .<br/>TLS uyarıları özelliği, .NET Framework 4,7 ' den başlayarak varsayılan olarak etkinleştirilmiştir. .NET Framework 4,7 veya daha yüksek bir sistemde çalışan 4,0 ile 4.6.2 arasında .NET Framework sürümlerini hedefleyen uygulamalar, uyumluluğu korumak için özelliği devre dışı bırakmış olur. <br/>Aşağıdaki yapılandırma API 'SI, .NET Framework 4,7 veya sonraki sürümlerde çalışan .NET Framework 4,6 ve üzeri uygulamalar için özelliği etkinleştirmek veya devre dışı bırakmak için kullanılabilir.

- Program aracılığıyla: ServicePointManager 'ın yalnızca bir kez başlatılmasından itibaren uygulamanın en ilk ne kadar tek şey olması gerekir:

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- AppConfig

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- Kayıt defteri anahtarı (makine genel): `false` .NET Framework 4,6-4.6.2 ' deki özelliği etkinleştirmek Için değerini olarak ayarlayın.

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
