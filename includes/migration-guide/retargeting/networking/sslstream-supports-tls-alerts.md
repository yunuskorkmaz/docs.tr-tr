---
ms.openlocfilehash: 136ffc9305de79679ac9d254c026ecb0debc7c52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235494"
---
### <a name="sslstream-supports-tls-alerts"></a>SslStream TLS Uyarılarını destekliyor

|   |   |
|---|---|
|Ayrıntılar|Başarısız bir TLS el <xref:System.IO.IOException?displayProperty=name> sıkışması <xref:System.ComponentModel.Win32Exception?displayProperty=name> ndan sonra, ilk G/Ç Okuma/Yazma işlemi tarafından içsel bir istisna ile atılır. Bunun <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=name> <xref:System.ComponentModel.Win32Exception?displayProperty=name> [kodu, TLS ve SSL uyarıları için Schannel hata kodları](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts)kullanılarak uzak taraftan TLS Uyarısı'na eşlenebilir. Daha fazla bilgi için [Bkz. RFC 2246: Bölüm 7.2.2 Hata uyarıları.](https://tools.ietf.org/html/rfc2246#section-7.2.2) <br/>.NET Framework 4.6.2 ve önceki davranış, aktarım kanalının (genellikle TCP bağlantısı) diğer tarafın el sıkışmada başarısız olup olmadığını ve hemen ardından bağlantıyı reddetmesi durumunda Yaz veya Oku sırasında zaman alacaktır.|
|Öneri|Ağ G/Ç API'lerini <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> çağıran <xref:System.IO.IOException> uygulamalar <xref:System.TimeoutException?displayProperty=name>gibi işleyebilir veya .<br/>TLS Uyarıları özelliği ,NET Framework 4.7 ile başlayarak varsayılan olarak etkinleştirilir. .NET Framework 4.0 ile 4.6.2 arasında bir .NET Framework 4.7 veya daha yüksek sistemde çalışan .NET Framework sürümlerini hedefleyen uygulamalar, uyumluluğu korumak için özelliği devre dışı bırakılır. <br/>.NET Framework 4.6 ve sonraki uygulamalar için .NET Framework 4.7 veya sonraki uygulamalar için aşağıdaki yapılandırma API'si kullanılabilir.<ul><li>Programlı olarak:</li></ul>ServicePointManager yalnızca bir kez başlatılması beri uygulama yapar ilk şey olmalıdır:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;TestSwitch.LocalAppContext.DisableCaching&quot;, true);&#13;&#10;AppContext.SetSwitch(&quot;Switch.System.Net.DontEnableTlsAlerts&quot;, true); // Set to &#39;false&#39; to enable the feature in .NET Framework 4.6 - 4.6.2.&#13;&#10;</code></pre><ul><li>AppConfig:</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableTlsAlerts=true&quot;/&gt;&#13;&#10;&lt;!-- Set to &#39;false&#39; to enable the feature in .NET Framework 4.6 - 4.6.2. --&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><ul><li>Kayıt defteri anahtarı (makine genel):</li></ul>.NET Framework <code>false</code> 4.6 - 4.6.2'deki özelliği etkinleştirmek için Değeri ayarlayın.<ul><li>Anahtar: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts</li><li>Türü: Dize</li><li>Değer: &quot;true&quot;</li></ul>|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.WebRequest?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.Http?displayProperty=nameWithType></li></ul>|
