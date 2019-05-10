---
title: 'Azaltma: TLS protokolleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b21dc73454b96d3a192b47eb439bebf588059c24
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599604"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="d275e-102">Azaltma: TLS protokolleri</span><span class="sxs-lookup"><span data-stu-id="d275e-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="d275e-103">.NET Framework 4.6 ile başlayan <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıfları aşağıdaki üç protokolden birini kullanmak için izin verilir: Tls1.0, Tls1.1 veya Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="d275e-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="d275e-104">SSL3.0 protokolünün ve RC4 şifreleme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d275e-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d275e-105">Etki</span><span class="sxs-lookup"><span data-stu-id="d275e-105">Impact</span></span>  
 <span data-ttu-id="d275e-106">Bu değişiklik etkiler:</span><span class="sxs-lookup"><span data-stu-id="d275e-106">This change affects:</span></span>  
  
- <span data-ttu-id="d275e-107">Bir HTTPS sunucusu ya da aşağıdaki türlerinden herhangi birini kullanarak bir yuva sunucusu konuşmak için SSL kullanan tüm uygulamalarda: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, ve <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="d275e-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="d275e-108">Tls1.0, Tls1.1 veya Tls 1.2 desteklemek için yükseltilemez herhangi bir sunucu tarafı uygulama...</span><span class="sxs-lookup"><span data-stu-id="d275e-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d275e-109">Azaltma</span><span class="sxs-lookup"><span data-stu-id="d275e-109">Mitigation</span></span>  
 <span data-ttu-id="d275e-110">Önerilen risk azaltma Tls1.0, Tls1.1 veya Tls 1.2 sunucu tarafı uygulamayı yükseltmektir.</span><span class="sxs-lookup"><span data-stu-id="d275e-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="d275e-111">Bu uygun değilse veya istemci uygulamaları kopmuş <xref:System.AppContext> sınıfı, bu özellik iki yöntemden biriyle dışında kabul etmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d275e-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="d275e-112">Programlı olarak aşağıdaki gibi bir kod parçacığını kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d275e-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="d275e-113">Çünkü <xref:System.Net.ServicePointManager> nesne yalnızca bu uyumluluk ayarlarını tanımlama uygulamasının yapacağı ilk şey bir kez olmalıdır başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d275e-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="d275e-114">Aşağıdaki satırı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config dosyanıza bölümünü:</span><span class="sxs-lookup"><span data-stu-id="d275e-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="d275e-115">Ancak, uygulama daha az güvenli kolaylaştırır olduğundan varsayılan davranışı iptal edilmesiyle, önerilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d275e-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d275e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d275e-116">See also</span></span>

- [<span data-ttu-id="d275e-117">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="d275e-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
