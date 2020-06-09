---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: cb7019f1e4b47bde7c98b0109afa7b0125b7ef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84577311"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="ce21e-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="ce21e-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="ce21e-103">Olası bir komşuyla güvenlik el sıkışması başarılı olmadı.</span><span class="sxs-lookup"><span data-stu-id="ce21e-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ce21e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce21e-104">Description</span></span>  
 <span data-ttu-id="ce21e-105">Bu izleme, güvenli bir komşu bağlantı kurmaya çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="ce21e-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="ce21e-106">Bu durum yetersiz veya hatalı kimlik bilgileri nedeniyle oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ce21e-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="ce21e-107">PeerChannel, uygulanabilen kimlik doğrulaması ve yetkilendirme türüne göre güçlü bir kimlik modeli sağlayan, güçlü tanımlama, X. 509.440 sertifikaları için tek bir belirteç türünü tanır.</span><span class="sxs-lookup"><span data-stu-id="ce21e-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="ce21e-108">PeerChannel Ayrıca parolaların kullanımı aracılığıyla basit uygulamalar için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce21e-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="ce21e-109">Parolalar yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması yapmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ce21e-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="ce21e-110">Bunun nedeni, bir eş payı grubunun paylaştığı bir simetrik belirtecin zor ve kaynak kimlik doğrulaması için kullanılmak üzere uygun olmadığı bir değer.</span><span class="sxs-lookup"><span data-stu-id="ce21e-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ce21e-111">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="ce21e-111">Troubleshooting</span></span>  
 <span data-ttu-id="ce21e-112">Tüm komşuların uygun güvenlik kimlik bilgilerine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ce21e-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce21e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce21e-113">See also</span></span>

- [<span data-ttu-id="ce21e-114">Eş Kanalı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ce21e-114">Peer Channel Security</span></span>](../../feature-details/peer-channel-security.md)
- [<span data-ttu-id="ce21e-115">İzleme</span><span class="sxs-lookup"><span data-stu-id="ce21e-115">Tracing</span></span>](index.md)
- [<span data-ttu-id="ce21e-116">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ce21e-116">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ce21e-117">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="ce21e-117">Administration and Diagnostics</span></span>](../index.md)
