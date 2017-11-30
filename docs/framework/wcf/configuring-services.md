---
title: "Hizmetleri Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0783107d22f2d64dd8ba7936ce7d2a283f6d8317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-services"></a><span data-ttu-id="94d0a-102">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="94d0a-102">Configuring Services</span></span>
<span data-ttu-id="94d0a-103">Tasarlanmış ve hizmet sözleşmesini uygulanmış sonra hizmetiniz yapılandırmaya hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="94d0a-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="94d0a-104">Burada tanımlayın ve hizmetinizi burada bulunabilir, taşıma ve iletileri ve gerektirdiği güvenlik türünü göndermek ve almak için kullandığı ileti kodlama adresini belirtme dahil olmak üzere istemcilere nasıl kullanıma sunulan özelleştirme budur.</span><span class="sxs-lookup"><span data-stu-id="94d0a-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="94d0a-105">Yapılandırma burada kullanılan gibi imperatively kodda veya tanımlama ve belirtme, uç nokta adresleri, kullanılan aktarımları ve kendi güvenlik düzenleri gibi bir hizmet çeşitli yönlerini özelleştirme bir yapılandırma dosyası kullanarak tüm yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="94d0a-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="94d0a-106">Uygulamada, yazma yapılandırma programlama önemli bir parçası olan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="94d0a-106">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94d0a-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="94d0a-107">In This Section</span></span>  
 [<span data-ttu-id="94d0a-108">Basitleştirilmiş yapılandırma</span><span class="sxs-lookup"><span data-stu-id="94d0a-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="94d0a-109">İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kolaylaştıran yeni bir varsayılan yapılandırma modeli ile birlikte gelen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yapılandırma gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="94d0a-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="94d0a-110">Herhangi bir belirtmezseniz, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] çalışma zamanı belirli bir hizmet yapılandırmasını varsayılan uç noktalar, bağlamaları ve davranışları hizmetinizi otomatik olarak yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="94d0a-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="94d0a-111">Yapılandırma dosyalarını kullanarak hizmetleri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="94d0a-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="94d0a-112">A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmetidir yapılandırılabilir kullanarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknolojisi.</span><span class="sxs-lookup"><span data-stu-id="94d0a-112">A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="94d0a-113">XML öğeleri barındıran Internet Information Services (IIS) sitesi için Web.config dosyasının en yaygın olarak eklenen bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="94d0a-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="94d0a-114">Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek bir makine Makineli temelinde izin verin.</span><span class="sxs-lookup"><span data-stu-id="94d0a-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="94d0a-115">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="94d0a-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="94d0a-116">Ayrıca, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hızlı bir şekilde nasıl bir istemci ve hizmet, aktarımları gibi güvenlik, iletişim için en temel özelliklerini seçmenize olanak tanır ve ileti Kodlamalar bağlamaları formunda birkaç sistem tarafından sağlanan ortak yapılandırmaları içerir kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94d0a-116">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="94d0a-117">Uç noktaları</span><span class="sxs-lookup"><span data-stu-id="94d0a-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="94d0a-118">İle tüm iletişimin bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] servis oluşur aracılığıyla *uç noktaları* hizmetinin.</span><span class="sxs-lookup"><span data-stu-id="94d0a-118">All communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="94d0a-119">Uç noktaları sözleşme, bağlamaları belirtilen yapılandırma bilgilerini ve hizmet nerede bulacağını veya hizmeti hakkında bilgi almak nereye belirtmek adresleri içerir.</span><span class="sxs-lookup"><span data-stu-id="94d0a-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="94d0a-120">Hizmetleri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="94d0a-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="94d0a-121">Kullanarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ve mevcut güvenlik mekanizmaları, gizlilik, bütünlük, kimlik doğrulama ve yetkilendirme herhangi bir hizmet uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94d0a-121">Using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="94d0a-122">Ayrıca, güvenlik başarı ve başarısızlık için de denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94d0a-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="94d0a-123">WS oluşturma-ı temel Profil 1.1 birlikte çalışabilir hizmetler</span><span class="sxs-lookup"><span data-stu-id="94d0a-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="94d0a-124">Birlikte çalışabilir hizmetler ve istemcileri herhangi bir platform veya işletim sistemi ile bir hizmeti dağıtma gereksinimleri WS özetlenen-ı temel Profil 1.1 belirtimini.</span><span class="sxs-lookup"><span data-stu-id="94d0a-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="94d0a-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="94d0a-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="94d0a-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="94d0a-126">Related Sections</span></span>  
 [<span data-ttu-id="94d0a-127">Temel programlama yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="94d0a-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="94d0a-128">Hizmetleri Tasarlama ve uygulama</span><span class="sxs-lookup"><span data-stu-id="94d0a-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="94d0a-129">Barındırma hizmetleri</span><span class="sxs-lookup"><span data-stu-id="94d0a-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="94d0a-130">İstemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="94d0a-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="94d0a-131">Genişletilebilirlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="94d0a-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="94d0a-132">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="94d0a-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="94d0a-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94d0a-133">See Also</span></span>  
 [<span data-ttu-id="94d0a-134">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="94d0a-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="94d0a-135">Kavramsal genel bakış</span><span class="sxs-lookup"><span data-stu-id="94d0a-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="94d0a-136">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="94d0a-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
