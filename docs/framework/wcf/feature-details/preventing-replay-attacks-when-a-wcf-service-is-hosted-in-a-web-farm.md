---
title: "Bir WCF Hizmeti Bir Web Grubunda Barındırıldığında Yeniden Yürütme Saldırılarını Önleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 383a93bee7a63bef966f4252ace13105d96ae505
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a><span data-ttu-id="12d34-102">Bir WCF Hizmeti Bir Web Grubunda Barındırıldığında Yeniden Yürütme Saldırılarını Önleme</span><span class="sxs-lookup"><span data-stu-id="12d34-102">Preventing Replay Attacks When a WCF Service is Hosted in a Web Farm</span></span>
<span data-ttu-id="12d34-103">Ne zaman ileti güvenliği WCF engel yeniden yürütme saldırılarını gelen ileti dışında NONCE oluşturma ve iç denetimi `InMemoryNonceCache` oluşturulan NONCE mevcut olup olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="12d34-103">When using message security WCF prevents replay attacks by creating a NONCE out of the incoming message and checking the internal `InMemoryNonceCache` to see if the generated NONCE is present.</span></span> <span data-ttu-id="12d34-104">İse, ileti yeniden yürütme atılır.</span><span class="sxs-lookup"><span data-stu-id="12d34-104">If it is, the message is discarded as a replay.</span></span> <span data-ttu-id="12d34-105">Ne zaman bir WCF Hizmeti barındırılan bir web grubunda beri `InMemoryNonceCache` paylaşılmayan web grubundaki düğümleri arasında hizmet yeniden yürütme saldırılarına karşı savunmasızdır.</span><span class="sxs-lookup"><span data-stu-id="12d34-105">When a WCF service is hosted in a web farm, since the `InMemoryNonceCache` is not shared across the nodes in the web farm, the service is vulnerable to replay attacks.</span></span>  <span data-ttu-id="12d34-106">Bu senaryo azaltmak için WCF 4.5 soyut sınıftan sınıf türetme tarafından paylaşılan kendi NONCE önbellek uygulamak izin veren bir genişletilebilirlik noktasıdır <xref:System.ServiceModel.Security.NonceCache>.</span><span class="sxs-lookup"><span data-stu-id="12d34-106">To mitigate this scenario WCF 4.5 provides an extensibility point that allows you to implement your own shared NONCE cache by deriving a class from the abstract class <xref:System.ServiceModel.Security.NonceCache>.</span></span>  
  
## <a name="noncecache-implementation"></a><span data-ttu-id="12d34-107">NonceCache uygulama</span><span class="sxs-lookup"><span data-stu-id="12d34-107">NonceCache Implementation</span></span>  
 <span data-ttu-id="12d34-108">Kendi paylaşılan NONCE önbellek uygulamak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Security.NonceCache> ve geçersiz kılma <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> ve <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="12d34-108">To implement your own shared NONCE cache, derive a class from <xref:System.ServiceModel.Security.NonceCache> and override the <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> and <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> methods.</span></span> <span data-ttu-id="12d34-109"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A>Belirtilen NONCE önbellekte olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="12d34-109"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> will check to see if the specified NONCE exists in the cache.</span></span> <span data-ttu-id="12d34-110"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>NONCE önbelleğe eklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="12d34-110"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> will attempt to add a NONCE to the cache.</span></span> <span data-ttu-id="12d34-111">Sınıfı uygulandıktan sonra onu bir örneği başlatmasını ve kendisine atayarak takma <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> için istemci tarafı yeniden yürütme algılaması ve <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> için sunucu tarafı yeniden yürütme algılaması.</span><span class="sxs-lookup"><span data-stu-id="12d34-111">Once the class is implemented, you hook it up by instantiating an instance and assigning it to <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> for client-side replay detection and <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> for server-side replay detection.</span></span> <span data-ttu-id="12d34-112">Bu özellik kutusunu yapılandırma desteği yok dışı yoktur.</span><span class="sxs-lookup"><span data-stu-id="12d34-112">There is no out of the box configuration support for this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d34-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12d34-113">See Also</span></span>  
 [<span data-ttu-id="12d34-114">İleti güvenliği</span><span class="sxs-lookup"><span data-stu-id="12d34-114">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="12d34-115">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="12d34-115">SymmetricSecurityBindingElement</span></span>](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
