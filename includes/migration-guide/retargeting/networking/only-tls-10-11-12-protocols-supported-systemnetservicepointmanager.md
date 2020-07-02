---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615763"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a><span data-ttu-id="eb46b-101">System .net. ServicePointManager ve System .net. Security. SslStream içinde yalnızca TLS 1,0, 1,1 ve 1,2 protokolleri desteklenir</span><span class="sxs-lookup"><span data-stu-id="eb46b-101">Only Tls 1.0, 1.1 and 1.2 protocols supported in System.Net.ServicePointManager and System.Net.Security.SslStream</span></span>

#### <a name="details"></a><span data-ttu-id="eb46b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="eb46b-102">Details</span></span>

<span data-ttu-id="eb46b-103">.NET Framework 4,6 ' den başlayarak, <xref:System.Net.ServicePointManager> ve <xref:System.Net.Security.SslStream> sınıflarının yalnızca şu üç protokolden birini kullanmasına izin verilir: TLS 1.0, TLS 1.1 veya TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="eb46b-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager> and <xref:System.Net.Security.SslStream> classes are only allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="eb46b-104">SSL 3.0 protokol ve RC4 şifresi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="eb46b-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eb46b-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="eb46b-105">Suggestion</span></span>

<span data-ttu-id="eb46b-106">Önerilen risk azaltma, sunucu tarafı uygulamayı TLS 1.0, TLS 1.1 veya TLS 1.2 sürümüne yükseltmek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="eb46b-106">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="eb46b-107">Bu uygun değilse veya istemci uygulamaları bozulur, <xref:System.AppContext?displayProperty=fullName> sınıfı iki şekilde bu özelliği devre dışı bırakmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="eb46b-107">If this is not feasible, or if client apps are broken, the <xref:System.AppContext?displayProperty=fullName> class can be used to opt out of this feature in either of two ways:</span></span>

- <span data-ttu-id="eb46b-108"><xref:System.AppContext?displayProperty=fullName> [Burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)açıklandığı gibi, üzerinde uyumluluk anahtarlarını programlı olarak ayarlayarak.</span><span class="sxs-lookup"><span data-stu-id="eb46b-108">By programmatically setting compat switches on the <xref:System.AppContext?displayProperty=fullName>, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="eb46b-109">`<runtime>`app.config dosyanın bölümüne aşağıdaki satırı ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="eb46b-109">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| <span data-ttu-id="eb46b-110">Name</span><span class="sxs-lookup"><span data-stu-id="eb46b-110">Name</span></span>    | <span data-ttu-id="eb46b-111">Değer</span><span class="sxs-lookup"><span data-stu-id="eb46b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eb46b-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="eb46b-112">Scope</span></span>   | <span data-ttu-id="eb46b-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="eb46b-113">Minor</span></span>       |
| <span data-ttu-id="eb46b-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="eb46b-114">Version</span></span> | <span data-ttu-id="eb46b-115">4.6</span><span class="sxs-lookup"><span data-stu-id="eb46b-115">4.6</span></span>         |
| <span data-ttu-id="eb46b-116">Tür</span><span class="sxs-lookup"><span data-stu-id="eb46b-116">Type</span></span>    | <span data-ttu-id="eb46b-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="eb46b-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="eb46b-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="eb46b-118">Affected APIs</span></span>

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
