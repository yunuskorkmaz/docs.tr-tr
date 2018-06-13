---
title: Hizmetleri Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 7718edaefbad18afa11b3e3680fac39da585a610
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803286"
---
# <a name="configuring-services"></a><span data-ttu-id="34fe6-102">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34fe6-102">Configuring Services</span></span>
<span data-ttu-id="34fe6-103">Tasarlanmış ve hizmet sözleşmesini uygulanmış sonra hizmetiniz yapılandırmaya hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="34fe6-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="34fe6-104">Burada tanımlayın ve hizmetinizi burada bulunabilir, taşıma ve iletileri ve gerektirdiği güvenlik türünü göndermek ve almak için kullandığı ileti kodlama adresini belirtme dahil olmak üzere istemcilere nasıl kullanıma sunulan özelleştirme budur.</span><span class="sxs-lookup"><span data-stu-id="34fe6-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="34fe6-105">Yapılandırma burada kullanılan gibi imperatively kodda veya tanımlama ve belirtme, uç nokta adresleri, kullanılan aktarımları ve kendi güvenlik düzenleri gibi bir hizmet çeşitli yönlerini özelleştirme bir yapılandırma dosyası kullanarak tüm yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="34fe6-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="34fe6-106">Bir ana uygulamada, yazma yapılandırmadır WCF uygulamalarını programlama parçası.</span><span class="sxs-lookup"><span data-stu-id="34fe6-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34fe6-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="34fe6-107">In This Section</span></span>  
 [<span data-ttu-id="34fe6-108">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34fe6-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="34fe6-109">İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, WCF yapılandırma gereksinimleri kolaylaştıran yeni bir varsayılan yapılandırma modeli ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="34fe6-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="34fe6-110">Belirli bir hizmet için herhangi bir WCF yapılandırma belirtmezseniz, çalışma zamanı varsayılan uç noktalar, bağlamaları ve davranışları ile otomatik olarak hizmetinizi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="34fe6-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="34fe6-111">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34fe6-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="34fe6-112">Windows Communication Foundation (WCF) hizmetini yapılandırılabilir kullanmaktır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknolojisi.</span><span class="sxs-lookup"><span data-stu-id="34fe6-112">A Windows Communication Foundation (WCF) service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="34fe6-113">En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran Internet Information Services (IIS) sitesi için Web.config dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="34fe6-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="34fe6-114">Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek bir makine Makineli temelinde izin verin.</span><span class="sxs-lookup"><span data-stu-id="34fe6-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="34fe6-115">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="34fe6-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="34fe6-116">Ayrıca, WCF en temel özellikleri nasıl bir istemci ve hizmet iletişim kurmak için aktarımları, güvenlik ve Kodlamalar kullanılan ileti gibi hızlı bir şekilde seçmenize olanak bağlamaları biçiminde birkaç sistem tarafından sağlanan ortak yapılandırmaları içerir.</span><span class="sxs-lookup"><span data-stu-id="34fe6-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="34fe6-117">Uç Noktalar</span><span class="sxs-lookup"><span data-stu-id="34fe6-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="34fe6-118">Tüm WCF Hizmeti ile aracılığıyla iletişimin *uç noktaları* hizmetinin.</span><span class="sxs-lookup"><span data-stu-id="34fe6-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="34fe6-119">Uç noktaları sözleşme, bağlamaları belirtilen yapılandırma bilgilerini ve hizmet nerede bulacağını veya hizmeti hakkında bilgi almak nereye belirtmek adresleri içerir.</span><span class="sxs-lookup"><span data-stu-id="34fe6-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="34fe6-120">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="34fe6-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="34fe6-121">WCF kullanarak ve mevcut güvenlik mekanizmaları gizliliğini, bütünlüğünü, kimlik doğrulama ve yetkilendirme herhangi bir hizmet uygulamasına uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34fe6-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="34fe6-122">Ayrıca, güvenlik başarı ve başarısızlık için de denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34fe6-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="34fe6-123">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="34fe6-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="34fe6-124">Birlikte çalışabilir hizmetler ve istemcileri herhangi bir platform veya işletim sistemi ile bir hizmeti dağıtma gereksinimleri WS özetlenen-ı temel Profil 1.1 belirtimini.</span><span class="sxs-lookup"><span data-stu-id="34fe6-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="34fe6-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="34fe6-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="34fe6-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="34fe6-126">Related Sections</span></span>  
 [<span data-ttu-id="34fe6-127">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="34fe6-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="34fe6-128">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="34fe6-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="34fe6-129">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="34fe6-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="34fe6-130">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="34fe6-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="34fe6-131">Genişletilebilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="34fe6-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="34fe6-132">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="34fe6-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="34fe6-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34fe6-133">See Also</span></span>  
 [<span data-ttu-id="34fe6-134">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="34fe6-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="34fe6-135">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="34fe6-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="34fe6-136">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="34fe6-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
