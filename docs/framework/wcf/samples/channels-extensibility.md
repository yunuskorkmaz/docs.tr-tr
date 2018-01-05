---
title: "Kanal Genişletilebilirliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 541770db6b9cc624fd08ab4db275bc63fa5deca9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="channels-extensibility"></a><span data-ttu-id="a4c45-102">Kanal Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="a4c45-102">Channels Extensibility</span></span>
<span data-ttu-id="a4c45-103">Bu bölüm, özel kanalları gösteren örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a4c45-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4c45-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a4c45-104">In This Section</span></span>  
 [<span data-ttu-id="a4c45-105">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="a4c45-105">Local Channel</span></span>](../../../../docs/framework/wcf/samples/local-channel.md)  
 <span data-ttu-id="a4c45-106">Yerel kanal gösteren bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aynı uygulama etki alanı içinde iletişim için kullanılan taşıma kanalı.</span><span class="sxs-lookup"><span data-stu-id="a4c45-106">Demonstrates the local channel, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="a4c45-107">Güvenilir Güvenlik Profili</span><span class="sxs-lookup"><span data-stu-id="a4c45-107">Reliable Secure Profile</span></span>](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 <span data-ttu-id="a4c45-108">Oluşturmak nasıl gösteren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve güvenilir güvenli profil (RSP).</span><span class="sxs-lookup"><span data-stu-id="a4c45-108">Demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="a4c45-109">Özel Kanal Dağıtıcı</span><span class="sxs-lookup"><span data-stu-id="a4c45-109">Custom Channel Dispatcher</span></span>](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 <span data-ttu-id="a4c45-110">Kanal yığını özel bir şekilde uygulayarak nasıl oluşturulacağını gösteren <xref:System.ServiceModel.ServiceHostBase> doğrudan ve Web ana bilgisayar ortamında özel kanal dağıtıcı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a4c45-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="a4c45-111">Öbekleme Kanalı</span><span class="sxs-lookup"><span data-stu-id="a4c45-111">Chunking Channel</span></span>](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 <span data-ttu-id="a4c45-112">Büyük iletileri kullanılarak gönderilen arabelleğe almak için kullanılan bellek miktarını sınırlamak gösterilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4c45-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="a4c45-113">HTTP Doğrulama Kanalı</span><span class="sxs-lookup"><span data-stu-id="a4c45-113">HTTP Acknowledgement Channel</span></span>](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 <span data-ttu-id="a4c45-114">Tek yönlü Mesajlaşma düzeni Değişeni katmanlı bir kanal gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4c45-114">Demonstrates a layered channel which changes the one-way messaging pattern.</span></span>  
  
 [<span data-ttu-id="a4c45-115">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="a4c45-115">HttpCookieSession</span></span>](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 <span data-ttu-id="a4c45-116">Özel protokol kanalı oturum yönetimi için HTTP tanımlama bilgilerini kullanacak şekilde nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4c45-116">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="a4c45-117">Özel İleti Kesici</span><span class="sxs-lookup"><span data-stu-id="a4c45-117">Custom Message Interceptor</span></span>](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 <span data-ttu-id="a4c45-118">Kanal fabrikaları ve çalışma zamanı yığınında belirli bir noktada tüm gelen ve giden iletileri izlemesine kanal dinleyicileri oluşturur özel bağlama öğesi uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a4c45-118">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
