---
ms.openlocfilehash: e86542cbf96025247a29a860bfd44db5383c9d16
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760326"
---
### <a name="sslstream-supports-tls-alerts"></a>TLS uyarılar SslStream destekler

|   |   |
|---|---|
|Ayrıntılar|Başarısız bir TLS anlaşması sonra bir <xref:System.IO.IOException?displayProperty=name> bir iç ile <xref:System.ComponentModel.Win32Exception?displayProperty=name> ilk g/ç okuma/yazma işlemi tarafından özel durum oluşturulur. <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=name> İçin kod <xref:System.ComponentModel.Win32Exception?displayProperty=name> kullanarak uzak taraftan TLS uyarısı eşlenebilir [Schannel hata kodlarını TLS ve SSL uyarılar için](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts). Daha fazla bilgi için [RFC 2246: Bölüm 7.2.2 hata uyarıları](https://tools.ietf.org/html/rfc2246#section-7.2.2). <br/>.NET Framework 4.6.2 davranışı ve daha önce (genellikle, TCP bağlantısı) taşıma kanalının olacağı zaman aşımı yazma veya okuma sırasında tarafa el sıkışması başarısız oldu ve hemen ardından bağlantıyı reddetti.|
|Öneri|Çağıran uygulamalara ağ g/ç API'leri gibi <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> işleyeceğini <xref:System.IO.IOException> veya <xref:System.TimeoutException?displayProperty=name>.<br/>TLS uyarıları özelliği, .NET Framework 4.7 ile başlayarak varsayılan olarak etkindir. .NET Framework 4. 0'ile bir .NET Framework 4.7 ya da daha yüksek bir sistem üzerinde çalışan 4.6.2 sürümlerini hedefleyen uygulamalar, özellik uyumluluğu korumak için devre dışı olacaktır. <br/>Aşağıdaki yapılandırma API'si etkinleştirmek veya .NET Framework 4.6 ve .NET Framework 4.7 veya sonraki sürümlerde çalışan sonraki uygulamalar için özelliği devre dışı bırakmak kullanılabilir.<ul><li>Programlı olarak:</li></ul>ServicePointManager yalnızca bir kez başlatma beri uygulamasının yapacağı çok ilk şey olması gerekir:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;TestSwitch.LocalAppContext.DisableCaching&quot;, true);&#13;&#10;AppContext.SetSwitch(&quot;Switch.System.Net.DontEnableTlsAlerts&quot;, true); // Set to &#39;false&#39; to enable the feature in .NET Framework 4.6 - 4.6.2.&#13;&#10;</code></pre><ul><li>AppConfig:</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableTlsAlerts=true&quot;/&gt;&#13;&#10;&lt;!-- Set to &#39;false&#39; to enable the feature in .NET Framework 4.6 - 4.6.2. --&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><ul><li>Kayıt defteri anahtarı (makine genel):</p>Değerine <code>false</code> .NET Framework 4.6 - 4.6.2 özelliği etkinleştirmek için.<ul><li>> anahtarı: HKLM\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts</li><li>Tür: Dize</li><li>Değer: &quot;true & quot;</li></ul></ul> |
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.WebRequest?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.Http?displayProperty=nameWithType></li></ul>|
