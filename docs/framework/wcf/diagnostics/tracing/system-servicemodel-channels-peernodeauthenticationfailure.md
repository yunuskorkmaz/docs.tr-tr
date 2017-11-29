---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b09d7fc476d5eed7f7c534fdde46cb18eeac30d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="79ce1-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="79ce1-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="79ce1-103">Olası komşu ile güvenlik el sıkışması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="79ce1-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="79ce1-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79ce1-104">Description</span></span>  
 <span data-ttu-id="79ce1-105">Bu izleme, bir güvenli komşu bağlantısı kurmaya çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="79ce1-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="79ce1-106">Yetersiz veya yanlış kimlik bilgileri nedeniyle oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="79ce1-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="79ce1-107">PeerChannel'a tek bir belirteç türü güçlü kimlik için kimlik doğrulama ve yetkilendirme uygulanabilir türüne göre bir güçlü kimlik modeli sağlar X.509 sertifikalarını tanır.</span><span class="sxs-lookup"><span data-stu-id="79ce1-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="79ce1-108">PeerChannel'a, parolaları ile basit uygulamalar için de destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="79ce1-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="79ce1-109">Parolalar, yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması gerçekleştirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="79ce1-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="79ce1-110">Eşleri grubudur paylaşan simetrik belirteç zor ve kaynak kimlik doğrulaması için kullanılacak uygun olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="79ce1-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="79ce1-111">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="79ce1-111">Troubleshooting</span></span>  
 <span data-ttu-id="79ce1-112">Tüm Komşuları uygun güvenlik kimlik bilgilerini olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="79ce1-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ce1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79ce1-113">See Also</span></span>  
 [<span data-ttu-id="79ce1-114">Eş kanalı güvenliği</span><span class="sxs-lookup"><span data-stu-id="79ce1-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="79ce1-115">İzleme</span><span class="sxs-lookup"><span data-stu-id="79ce1-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="79ce1-116">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="79ce1-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="79ce1-117">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="79ce1-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
