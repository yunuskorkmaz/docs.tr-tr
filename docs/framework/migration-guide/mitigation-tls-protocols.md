---
title: 'Azaltma: TLS Protokolleri'
description: .NET Framework 4,6 ' den başlayarak TLS protokol değişikliklerinin etkileri ve hafifletme hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: bb5aab3361663d7b5401d7e68688265fbc65b36f
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475365"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="e6498-103">Azaltma: TLS Protokolleri</span><span class="sxs-lookup"><span data-stu-id="e6498-103">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="e6498-104">.NET Framework 4,6 ' den başlayarak, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıflarının şu üç protokolden birini kullanmasına izin verilir: TLS 1.0, TLS 1.1 veya TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="e6498-104">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="e6498-105">SSL 3.0 protokol ve RC4 şifresi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e6498-105">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e6498-106">Etki</span><span class="sxs-lookup"><span data-stu-id="e6498-106">Impact</span></span>  
 <span data-ttu-id="e6498-107">Bu değişiklik şunları etkiler:</span><span class="sxs-lookup"><span data-stu-id="e6498-107">This change affects:</span></span>  
  
- <span data-ttu-id="e6498-108">SSL kullanan herhangi bir uygulama, aşağıdaki türlerden birini kullanarak bir https sunucusuyla veya bir yuva sunucusuyla iletişim kurabilir: <xref:System.Net.Http.HttpClient> ,,, <xref:System.Net.HttpWebRequest> <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient> ve <xref:System.Net.Security.SslStream> .</span><span class="sxs-lookup"><span data-stu-id="e6498-108">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="e6498-109">TLS 1.0, TLS 1.1 veya TLS 1,2 desteği için yükseltilemeyen herhangi bir sunucu tarafı uygulama.</span><span class="sxs-lookup"><span data-stu-id="e6498-109">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e6498-110">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="e6498-110">Mitigation</span></span>  
 <span data-ttu-id="e6498-111">Önerilen risk azaltma, sunucu tarafı uygulamayı TLS 1.0, TLS 1.1 veya TLS 1,2 sürümüne yükseltmekle birlikte önerilir.</span><span class="sxs-lookup"><span data-stu-id="e6498-111">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="e6498-112">Bu uygun değilse veya istemci uygulamaları bozulur, <xref:System.AppContext> sınıfı iki şekilde bu özelliği devre dışı bırakmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e6498-112">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="e6498-113">Programlı olarak, aşağıdaki gibi bir kod parçacığı kullanarak:</span><span class="sxs-lookup"><span data-stu-id="e6498-113">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="e6498-114"><xref:System.Net.ServicePointManager>Nesne yalnızca bir kez başlatıldığından, bu uyumluluk ayarlarının tanımlanması uygulamanın ilk tarafından yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6498-114">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="e6498-115">[\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md)app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="e6498-115">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="e6498-116">Ancak, uygulamayı daha az güvenli hale yaptığından varsayılan davranışın yerine geçen önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e6498-116">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6498-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6498-117">See also</span></span>

- [<span data-ttu-id="e6498-118">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="e6498-118">Application compatibility</span></span>](application-compatibility.md)
