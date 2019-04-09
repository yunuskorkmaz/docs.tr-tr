---
title: WCF hizmetlerini yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 81727adbf985986a71cc9f9e2d42a1de0cb1fd76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156513"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="540ce-102">WCF hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="540ce-102">Configuring WCF services</span></span>

<span data-ttu-id="540ce-103">Tasarlanmış ve hizmet sözleşmeniz uygulanan sonra hizmetinizin yapılandırmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="540ce-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="540ce-104">Burada tanımlayın ve hizmetinizi burada bulunabilir, taşıma ve iletileri ve gerektiren güvenlik türünü göndermek ve almak için kullandığı ileti kodlama adresi belirtme dahil olmak üzere istemcilere nasıl kullanıma sunulan özelleştirme budur.</span><span class="sxs-lookup"><span data-stu-id="540ce-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="540ce-105">Yapılandırma burada kullanılan kesin kod veya tanımlayın ve bir hizmetin kendi güvenlik düzenleri, uç nokta adresleri ve kullanılan taşımalar belirleme gibi çeşitli yönlerini de özelleştirerek bir yapılandırma dosyası kullanarak tüm yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="540ce-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="540ce-106">Büyük bir uygulamada, yazma yapılandırmadır WCF uygulamalarını programlama parçası.</span><span class="sxs-lookup"><span data-stu-id="540ce-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="540ce-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="540ce-107">In This Section</span></span>  
 [<span data-ttu-id="540ce-108">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="540ce-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="540ce-109">İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, WCF yapılandırma gereksinimleri basitleştiren yeni bir varsayılan yapılandırma modeli ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="540ce-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="540ce-110">Belirli bir hizmet için herhangi bir WCF yapılandırma sağlamazsanız, çalışma zamanı varsayılan uç noktaları, bağlamalar ve davranışları ile otomatik olarak hizmetinizi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="540ce-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="540ce-111">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="540ce-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="540ce-112">Yapılandırılabilir kullanarak bir Windows Communication Foundation (WCF) hizmetidir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknoloji.</span><span class="sxs-lookup"><span data-stu-id="540ce-112">A Windows Communication Foundation (WCF) service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="540ce-113">En yaygın olarak, XML öğeleri, bir WCF hizmetini barındıran Internet Information Services (IIS) sitesi için Web.config dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="540ce-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="540ce-114">Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek makine tarafından makine olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="540ce-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="540ce-115">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="540ce-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="540ce-116">Ayrıca, WCF, hızlı bir şekilde nasıl bir istemci ve hizmet iletişim kurmak için aktarımlar, güvenlik ve kodlamaları kullanılan ileti gibi en temel özellikler seçmenizi sağlayacak bağlamaları biçiminde birçok sistem tarafından sağlanan genel yapılandırmaları içerir.</span><span class="sxs-lookup"><span data-stu-id="540ce-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="540ce-117">Uç Noktalar</span><span class="sxs-lookup"><span data-stu-id="540ce-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="540ce-118">Bir WCF Hizmeti ile tüm iletişimi üzerinden gerçekleşir *uç noktaları* hizmeti.</span><span class="sxs-lookup"><span data-stu-id="540ce-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="540ce-119">Uç noktaları, sözleşmenin bağlamaları belirtilen yapılandırma bilgilerini ve hizmet nerede bulacağını veya hizmet hakkında bilgi almak nereye belirtmek adresleri içerir.</span><span class="sxs-lookup"><span data-stu-id="540ce-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="540ce-120">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="540ce-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="540ce-121">WCF kullanan ve var olan güvenlik mekanizmaları, gizlilik, bütünlük, kimlik doğrulama ve yetkilendirme, herhangi bir hizmet uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="540ce-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="540ce-122">Ayrıca, güvenlik başarı ve başarısızlık için de denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="540ce-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="540ce-123">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="540ce-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="540ce-124">Hizmetler ve istemcileri herhangi bir platform veya işletim sistemi ile birlikte çalışabilen bir hizmeti dağıtmak için gereksinimleri WS içinde ana hatlarıyla özetlenen-ı Basic Profile 1.1 belirtimi.</span><span class="sxs-lookup"><span data-stu-id="540ce-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="540ce-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="540ce-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="540ce-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="540ce-126">Related Sections</span></span>  
 [<span data-ttu-id="540ce-127">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="540ce-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="540ce-128">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="540ce-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="540ce-129">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="540ce-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="540ce-130">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="540ce-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="540ce-131">Genişletilebilirlik Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="540ce-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="540ce-132">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="540ce-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="540ce-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="540ce-133">See also</span></span>

- [<span data-ttu-id="540ce-134">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="540ce-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="540ce-135">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="540ce-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)
- [<span data-ttu-id="540ce-136">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="540ce-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
