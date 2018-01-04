---
title: 'Azaltma: TLS Protokolleri'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53a1100e40edb700d51fe907d3dc94c6216c4ebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="c1963-102">Azaltma: TLS Protokolleri</span><span class="sxs-lookup"><span data-stu-id="c1963-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="c1963-103">.NET Framework 4.6 ile başlayan <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıfları aşağıdaki üç protokolden birini kullanmasına izin: Tls1.0, Tls1.1 veya Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="c1963-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="c1963-104">RC4 şifreleme ve SSL3.0 protokolü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c1963-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c1963-105">Etki</span><span class="sxs-lookup"><span data-stu-id="c1963-105">Impact</span></span>  
 <span data-ttu-id="c1963-106">Bu değişiklik etkiler:</span><span class="sxs-lookup"><span data-stu-id="c1963-106">This change affects:</span></span>  
  
-   <span data-ttu-id="c1963-107">Bir HTTPS sunucusu ya da şu türlerden birini kullanarak yuva sunucusuna anlaşmak için SSL kullanan tüm uygulamalarda: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, ve <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="c1963-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
-   <span data-ttu-id="c1963-108">Tls1.0, Tls1.1 veya Tls 1.2 destekleyecek şekilde yükseltilemez herhangi bir sunucu tarafı uygulama...</span><span class="sxs-lookup"><span data-stu-id="c1963-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c1963-109">Azaltma</span><span class="sxs-lookup"><span data-stu-id="c1963-109">Mitigation</span></span>  
 <span data-ttu-id="c1963-110">Önerilen risk azaltma Tls1.0, Tls1.1 veya Tls 1.2 sunucu-tarafı uygulaması yükseltmektir.</span><span class="sxs-lookup"><span data-stu-id="c1963-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="c1963-111">Bu uygun olmadığı veya istemci uygulamaları koptu <xref:System.AppContext> sınıfı, bu özellik iki yoldan biriyle dışında kabul etmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c1963-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
-   <span data-ttu-id="c1963-112">Program aracılığıyla, aşağıdaki gibi kod parçacığını kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c1963-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="c1963-113">Çünkü <xref:System.Net.ServicePointManager> nesne başlatıldığı yalnızca bir kez, bu uyumluluk ayarlarını tanımlama uygulama yapacağı ilk şey olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1963-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
-   <span data-ttu-id="c1963-114">Aşağıdaki satırı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="c1963-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="c1963-115">Ancak, uygulama daha az güvenli kolaylaştırır beri dışında varsayılan davranışı kullanmama önerilmez olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c1963-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1963-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1963-116">See Also</span></span>  
 [<span data-ttu-id="c1963-117">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="c1963-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
