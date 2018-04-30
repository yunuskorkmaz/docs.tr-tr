---
title: WCF Özellik Ayrıntıları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- features [WCF]
- WCF, features
- Windows Communication Foundation, features
ms.assetid: 9b4368ca-0bd3-40dc-a539-bcd5779cee5f
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91b22cbcabba95d8cc91ffbc0b74b51e61dae393
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-feature-details"></a><span data-ttu-id="7bacf-102">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="7bacf-102">WCF Feature Details</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7bacf-103"> bir uygulama Mesajlaşma işlevlerini üzerinde kapsamlı denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bacf-103"> allows extensive control over the messaging functions of an application.</span></span> <span data-ttu-id="7bacf-104">Bu bölümdeki konular, kullanılabilir özellikleri hakkında ayrıntılı bilgi uygulamasına gidin.</span><span class="sxs-lookup"><span data-stu-id="7bacf-104">The topics in this section go into detail about the available features.</span></span> <span data-ttu-id="7bacf-105">Temel programlama hakkında daha fazla bilgi için bkz: [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="7bacf-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7bacf-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7bacf-106">In This Section</span></span>  
 [<span data-ttu-id="7bacf-107">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="7bacf-107">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 <span data-ttu-id="7bacf-108">İş akışı hizmetleri oluşturulacağı ve yapılandırılacağı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bacf-108">Describes how to create and configure workflow services.</span></span>  
  
 [<span data-ttu-id="7bacf-109">Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="7bacf-109">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 <span data-ttu-id="7bacf-110">Hizmet birden çok yönlerini kontrol açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bacf-110">Describes how to control multiple aspects of your service.</span></span>  
  
 [<span data-ttu-id="7bacf-111">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7bacf-111">Data Transfer and Serialization</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)  
 <span data-ttu-id="7bacf-112">Birlikte çalışabilirlik veya gelecekteki uyumluluk için seri hale getirme verilerinin nasıl uyarlanabilir açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bacf-112">Describes how serialization of data can be tailored for interoperation or future compatibility.</span></span>  
  
 [<span data-ttu-id="7bacf-113">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="7bacf-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 <span data-ttu-id="7bacf-114">Örnek oluşturma ve oturum modlarını açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve uygulamanız için doğru modu seçin.</span><span class="sxs-lookup"><span data-stu-id="7bacf-114">Describes the instancing and session modes of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and how to select the right mode for your application.</span></span>  
  
 [<span data-ttu-id="7bacf-115">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="7bacf-115">Transports</span></span>](../../../../docs/framework/wcf/feature-details/transports.md)  
 <span data-ttu-id="7bacf-116">Aktarım katmanı, kanal yığının en düşük düzeyde yapılandırılması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bacf-116">Describes how to configure the transport layer, the lowest level of the channel stack.</span></span>  
  
 [<span data-ttu-id="7bacf-117">Kuyruklar ve Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="7bacf-117">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)  
 <span data-ttu-id="7bacf-118">Alıcı uygulamanın adına gönderen bir uygulamadan gelen iletileri depolamak ve daha sonra bu iletileri alma işlemini yapan uygulamanın iletme sıralarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bacf-118">Describes queues, which store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span>  
  
 [<span data-ttu-id="7bacf-119">İşlemler</span><span class="sxs-lookup"><span data-stu-id="7bacf-119">Transactions</span></span>](../../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)  
 <span data-ttu-id="7bacf-120">Gerekirse geri alınabilir hizmetteki işlem oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bacf-120">Explains how to create transacted operations that can be rolled back if needed.</span></span>  
  
 [<span data-ttu-id="7bacf-121">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="7bacf-121">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 <span data-ttu-id="7bacf-122">Açıklar nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik gizliliği ve bütünlük sahip uygulamalar oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7bacf-122">Describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security helps you to create applications that have confidentiality and integrity.</span></span> <span data-ttu-id="7bacf-123">Ayrıca kimlik doğrulaması ve yetkilendirme özellikleri denetim olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bacf-123">Authentication and authorization are also available, as are auditing features.</span></span>  
  
 [<span data-ttu-id="7bacf-124">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="7bacf-124">Peer-to-Peer Networking</span></span>](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 <span data-ttu-id="7bacf-125">Hizmetler ve istemcileri eş oluşturma ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7bacf-125">Details how to create peer services and clients.</span></span>  
  
 [<span data-ttu-id="7bacf-126">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="7bacf-126">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 <span data-ttu-id="7bacf-127">Meta veri mimarisi ve biçimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bacf-127">Describes metadata architecture and formats.</span></span>  
  
 [<span data-ttu-id="7bacf-128">İstemciler</span><span class="sxs-lookup"><span data-stu-id="7bacf-128">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 <span data-ttu-id="7bacf-129">Çeşitli hizmetlere erişmesine istemciler oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bacf-129">Describes how to create a variety of clients that access services.</span></span>  
  
 [<span data-ttu-id="7bacf-130">Barındırma</span><span class="sxs-lookup"><span data-stu-id="7bacf-130">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 <span data-ttu-id="7bacf-131">Barındırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bacf-131">Describes hosting.</span></span> <span data-ttu-id="7bacf-132">Bir hizmet başka bir uygulama tarafından barındırılabilen veya kendi kendini barındıran olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bacf-132">A service can be hosted by another application, or it can be self-hosted.</span></span>  
  
 [<span data-ttu-id="7bacf-133">Birlikte Çalışabilirlik ve Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="7bacf-133">Interoperability and Integration</span></span>](../../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)  
 <span data-ttu-id="7bacf-134">Nasıl kullanılacağını açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] COM + barındırılan bir bileşen tabanlı uygulama mantığı önemli ölçüde yatırımınız varsa yeniden yazmaya gerek yerine mevcut mantığınızı genişletmek için.</span><span class="sxs-lookup"><span data-stu-id="7bacf-134">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to extend your existing logic rather than having to rewrite it if you have a substantial investment in component-based application logic hosted in COM+.</span></span>  
  
 [<span data-ttu-id="7bacf-135">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="7bacf-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 <span data-ttu-id="7bacf-136">Açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web programlama modeli kullanıma sunmak geliştiricilerin sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet dışı SOAP uç noktası işlemleri.</span><span class="sxs-lookup"><span data-stu-id="7bacf-136">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming Model that allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span>  
  
 [<span data-ttu-id="7bacf-137">WCF Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="7bacf-137">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 <span data-ttu-id="7bacf-138">Gelen dağıtım akışlarını kolayca kullanıma sunmak için destek açıklanır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="7bacf-138">Describes support to easily expose syndication feeds from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 [<span data-ttu-id="7bacf-139">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="7bacf-139">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 <span data-ttu-id="7bacf-140">ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) ve JavaScript nesne gösterimi (JSON) veri biçimi izin vermek için destek açıklanır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX istemcilere işlemlerinin açığa Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="7bacf-140">Describes support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format to allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span>  
  
 [<span data-ttu-id="7bacf-141">WCF Bulma</span><span class="sxs-lookup"><span data-stu-id="7bacf-141">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 <span data-ttu-id="7bacf-142">WS bulma protokolünü kullanarak bir birlikte çalışabilen şekilde çalışma zamanında bulunabilir olması hizmetleri etkinleştirmek için destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="7bacf-142">Describes support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span>  
  
 [<span data-ttu-id="7bacf-143">Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="7bacf-143">Routing</span></span>](../../../../docs/framework/wcf/feature-details/routing.md)  
 <span data-ttu-id="7bacf-144">Yönlendirme hizmeti açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bacf-144">Describes the routing service.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7bacf-145">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7bacf-145">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.ServiceModel.Routing>  
  
## <a name="related-sections"></a><span data-ttu-id="7bacf-146">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7bacf-146">Related Sections</span></span>  
 [<span data-ttu-id="7bacf-147">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="7bacf-147">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
