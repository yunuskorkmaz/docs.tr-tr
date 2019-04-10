---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 315122914ebcb3e8e4d72c8d976026a126306168
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219011"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="a82eb-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="a82eb-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="a82eb-103">Olası bir komşu ile güvenlik el sıkışması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a82eb-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a82eb-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a82eb-104">Description</span></span>  
 <span data-ttu-id="a82eb-105">Bu izleme, güvenli komşu bağlantısı kurmaya çalışırken ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="a82eb-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="a82eb-106">Bu, yetersiz ya da yanlış kimlik bilgileri nedeniyle oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="a82eb-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="a82eb-107">PeerChannel'a güçlü tanımlama için tek bir belirteç türü uygulanabilir yetkilendirme ve kimlik doğrulaması türüne göre bir güçlü kimlik modeli sağlayan X.509 sertifikalarını tanır.</span><span class="sxs-lookup"><span data-stu-id="a82eb-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="a82eb-108">PeerChannel'a parolaları kullanarak basit uygulamalar için de destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a82eb-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="a82eb-109">Parolaları, yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması gerçekleştirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a82eb-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="a82eb-110">Eşleri grubudur paylaştığı simetrik bir belirteç zor veya uygunsuz kaynak kimlik doğrulaması için kullanılacak olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a82eb-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a82eb-111">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="a82eb-111">Troubleshooting</span></span>  
 <span data-ttu-id="a82eb-112">Tüm Komşuları uygun güvenlik kimlik bilgilerini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a82eb-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a82eb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a82eb-113">See also</span></span>

- [<span data-ttu-id="a82eb-114">Eş Kanalı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a82eb-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [<span data-ttu-id="a82eb-115">İzleme</span><span class="sxs-lookup"><span data-stu-id="a82eb-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="a82eb-116">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="a82eb-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a82eb-117">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="a82eb-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
