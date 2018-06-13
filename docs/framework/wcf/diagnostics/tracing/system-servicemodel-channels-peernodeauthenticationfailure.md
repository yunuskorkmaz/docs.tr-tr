---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 633f497950ab14d7715537eed8f5cc80e7a350a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479859"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="e4fef-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="e4fef-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="e4fef-103">Olası komşu ile güvenlik el sıkışması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="e4fef-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e4fef-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4fef-104">Description</span></span>  
 <span data-ttu-id="e4fef-105">Bu izleme, bir güvenli komşu bağlantısı kurmaya çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="e4fef-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="e4fef-106">Yetersiz veya yanlış kimlik bilgileri nedeniyle oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="e4fef-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="e4fef-107">PeerChannel'a tek bir belirteç türü güçlü kimlik için kimlik doğrulama ve yetkilendirme uygulanabilir türüne göre bir güçlü kimlik modeli sağlar X.509 sertifikalarını tanır.</span><span class="sxs-lookup"><span data-stu-id="e4fef-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="e4fef-108">PeerChannel'a, parolaları ile basit uygulamalar için de destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4fef-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="e4fef-109">Parolalar, yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması gerçekleştirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e4fef-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="e4fef-110">Eşleri grubudur paylaşan simetrik belirteç zor ve kaynak kimlik doğrulaması için kullanılacak uygun olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e4fef-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e4fef-111">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="e4fef-111">Troubleshooting</span></span>  
 <span data-ttu-id="e4fef-112">Tüm Komşuları uygun güvenlik kimlik bilgilerini olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4fef-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4fef-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4fef-113">See Also</span></span>  
 [<span data-ttu-id="e4fef-114">Eş Kanalı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e4fef-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="e4fef-115">İzleme</span><span class="sxs-lookup"><span data-stu-id="e4fef-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e4fef-116">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="e4fef-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e4fef-117">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="e4fef-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
