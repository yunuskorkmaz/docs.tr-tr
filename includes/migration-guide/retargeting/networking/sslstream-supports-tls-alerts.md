---
ms.openlocfilehash: 5b566dd89801caff7a253abc2fb62c5fd79591f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606645"
---
### <a name="sslstream-supports-tls-alerts"></a><span data-ttu-id="b57be-101">SslStream TLS uyarılarını destekler</span><span class="sxs-lookup"><span data-stu-id="b57be-101">SslStream supports TLS Alerts</span></span>

#### <a name="details"></a><span data-ttu-id="b57be-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b57be-102">Details</span></span>

<span data-ttu-id="b57be-103">Başarısız bir TLS anlaşması sonrasında, <xref:System.IO.IOException?displayProperty=fullName> <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> ilk g/ç okuma/yazma işlemi tarafından iç özel durum içeren bir iç özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b57be-103">After a failed TLS handshake, an <xref:System.IO.IOException?displayProperty=fullName> with an inner <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> exception will be thrown by the first I/O Read/Write operation.</span></span> <span data-ttu-id="b57be-104"><xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName>İçin kodu, <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> [TLS ve SSL uyarıları için Schannel hata kodları](/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts)kullanılarak uzak tarafın TLS uyarısıyla eşleştirilebilir. Daha fazla bilgi için bkz. [RFC 2246: Bölüm 7.2.2 hata uyarıları](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span><span class="sxs-lookup"><span data-stu-id="b57be-104">The <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> code for the <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> can be mapped to the TLS Alert from the remote party using the [Schannel error codes for TLS and SSL alerts](/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts).For more information, see [RFC 2246: Section 7.2.2 Error alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span></span> <br/><span data-ttu-id="b57be-105">.NET Framework 4.6.2 ve önceki sürümlerde, taşıma kanalının (genellikle TCP bağlantısı) yazma veya okuma sırasında, diğer tarafın el sıkışması başarısız olması ve bağlantıyı reddetmesi sırasında zaman aşımına uğrayacağı bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="b57be-105">The behavior in .NET Framework 4.6.2 and earlier is that the transport channel (usually TCP connection) will timeout during either Write or Read if the other party failed the handshake and immediately afterwards rejected the connection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b57be-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="b57be-106">Suggestion</span></span>

<span data-ttu-id="b57be-107">Veya gibi ağ g/ç API 'lerini çağıran uygulamalar, <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> <xref:System.IO.IOException> veya <xref:System.TimeoutException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="b57be-107">Applications calling network I/O APIs such as <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> should handle <xref:System.IO.IOException> or <xref:System.TimeoutException?displayProperty=fullName>.</span></span><br/><span data-ttu-id="b57be-108">TLS uyarıları özelliği, .NET Framework 4,7 ' den başlayarak varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b57be-108">The TLS Alerts feature is enabled by default starting with .NET Framework 4.7.</span></span> <span data-ttu-id="b57be-109">.NET Framework 4,7 veya daha yüksek bir sistemde çalışan 4,0 ile 4.6.2 arasında .NET Framework sürümlerini hedefleyen uygulamalar, uyumluluğu korumak için özelliği devre dışı bırakmış olur.</span><span class="sxs-lookup"><span data-stu-id="b57be-109">Applications targeting versions of the .NET Framework from 4.0 through 4.6.2 running on a .NET Framework 4.7 or higher system will have the feature disabled to preserve compatibility.</span></span> <br/><span data-ttu-id="b57be-110">Aşağıdaki yapılandırma API 'SI, .NET Framework 4,7 veya sonraki sürümlerde çalışan .NET Framework 4,6 ve üzeri uygulamalar için özelliği etkinleştirmek veya devre dışı bırakmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b57be-110">The following configuration API is available to enable or disable the feature for .NET Framework 4.6 and later applications running on .NET Framework 4.7 or later.</span></span>

- <span data-ttu-id="b57be-111">Program aracılığıyla: ServicePointManager 'ın yalnızca bir kez başlatılmasından itibaren uygulamanın en ilk ne kadar tek şey olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="b57be-111">Programmatically:   Must be the very first thing the application does since ServicePointManager will initialize only once:</span></span>

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- <span data-ttu-id="b57be-112">AppConfig</span><span class="sxs-lookup"><span data-stu-id="b57be-112">AppConfig:</span></span>

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- <span data-ttu-id="b57be-113">Kayıt defteri anahtarı (makine genel): `false` .NET Framework 4,6-4.6.2 ' deki özelliği etkinleştirmek Için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b57be-113">Registry key (machine global):   Set the Value to `false` to enable the feature in .NET Framework 4.6 - 4.6.2.</span></span>

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| <span data-ttu-id="b57be-114">Name</span><span class="sxs-lookup"><span data-stu-id="b57be-114">Name</span></span>    | <span data-ttu-id="b57be-115">Değer</span><span class="sxs-lookup"><span data-stu-id="b57be-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b57be-116">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b57be-116">Scope</span></span>   | <span data-ttu-id="b57be-117">Edge</span><span class="sxs-lookup"><span data-stu-id="b57be-117">Edge</span></span>        |
| <span data-ttu-id="b57be-118">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b57be-118">Version</span></span> | <span data-ttu-id="b57be-119">4,7</span><span class="sxs-lookup"><span data-stu-id="b57be-119">4.7</span></span>         |
| <span data-ttu-id="b57be-120">Tür</span><span class="sxs-lookup"><span data-stu-id="b57be-120">Type</span></span>    | <span data-ttu-id="b57be-121">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="b57be-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b57be-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b57be-122">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
