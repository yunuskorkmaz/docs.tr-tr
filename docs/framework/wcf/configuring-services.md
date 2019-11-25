---
title: WCF hizmetlerini yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 332a88530010197187ca3ea787e152b0c95a5514
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141589"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="fa27d-102">WCF hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa27d-102">Configuring WCF services</span></span>

<span data-ttu-id="fa27d-103">Hizmet sözleşmenizi tasarladıktan ve uyguladıktan sonra, hizmetinizi yapılandırmaya hazırlanın.</span><span class="sxs-lookup"><span data-stu-id="fa27d-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="fa27d-104">Burada, hizmetinizin, bulunabileceği adresi belirtme, ileti göndermek ve almak için kullandığı Aktarım ve ileti kodlama ve gerek duyduğu güvenlik türü dahil olmak üzere, istemcilerin istemcilere sunulma şeklini tanımlamanız ve özelleştirmeniz burada yer alır.</span><span class="sxs-lookup"><span data-stu-id="fa27d-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="fa27d-105">Burada kullanılan yapılandırma, bir hizmetin uç nokta adreslerini, kullanılan taşımaları ve güvenlik düzenlerini belirtmek gibi bir hizmetin çeşitli yönlerini tanımlayabileceğiniz ve özelleştirebileceğiniz bir yapılandırma dosyası kullanarak tüm yolları, imperatively içinde veya bir yapılandırma dosyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="fa27d-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="fa27d-106">Uygulamada, yapılandırma yazma, WCF uygulamalarının Programlamanın önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="fa27d-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa27d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fa27d-107">In This Section</span></span>  
 [<span data-ttu-id="fa27d-108">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa27d-108">Simplified Configuration</span></span>](simplified-configuration.md)  
 <span data-ttu-id="fa27d-109">WCF, .NET Framework 4 ' te başlayarak WCF yapılandırma gereksinimlerini kolaylaştıran yeni bir varsayılan yapılandırma modeliyle gelir.</span><span class="sxs-lookup"><span data-stu-id="fa27d-109">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="fa27d-110">Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma zamanı hizmetinizi otomatik olarak varsayılan uç noktalar, bağlamalar ve davranışlar ile yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fa27d-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="fa27d-111">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa27d-111">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
 <span data-ttu-id="fa27d-112">Windows Communication Foundation (WCF) hizmeti, .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa27d-112">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="fa27d-113">En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran bir Internet Information Services (IIS) sitesi için Web. config dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="fa27d-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="fa27d-114">Öğeler, bir makine temelinde, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="fa27d-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="fa27d-115">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fa27d-115">Bindings</span></span>](bindings.md)  
 <span data-ttu-id="fa27d-116">Ayrıca, WCF, istemci ve hizmetin nasıl iletişim kurduğu, aktarımlar, güvenlik ve ileti kodlamaları gibi en temel özellikleri hızlı bir şekilde seçmenizi sağlayan bağlamalar biçiminde sistem tarafından sunulan birçok ortak yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="fa27d-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="fa27d-117">Uç Noktalar</span><span class="sxs-lookup"><span data-stu-id="fa27d-117">Endpoints</span></span>](endpoints.md)  
 <span data-ttu-id="fa27d-118">WCF hizmeti ile kurulan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur.</span><span class="sxs-lookup"><span data-stu-id="fa27d-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="fa27d-119">Uç noktalar sözleşmeyi, bağlamalarda belirtilen yapılandırma bilgilerini ve hizmetin nerede bulunacağını veya hizmet hakkındaki bilgilerin nerede alınacağını belirten adresleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fa27d-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="fa27d-120">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fa27d-120">Securing Services</span></span>](securing-services.md)  
 <span data-ttu-id="fa27d-121">WCF ve mevcut güvenlik mekanizmalarını kullanarak, herhangi bir hizmete gizlilik, bütünlük, kimlik doğrulama ve yetkilendirme uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa27d-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="fa27d-122">Ayrıca güvenlik başarıları ve başarısızlıklarını da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa27d-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="fa27d-123">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa27d-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="fa27d-124">Diğer platformların veya işletim sistemindeki hizmetler ve istemcilerle birlikte çalışabilen bir hizmeti dağıtmaya yönelik gereksinimler, WS-ı temel profil 1,1 belirtiminde özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa27d-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fa27d-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="fa27d-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="fa27d-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fa27d-126">Related Sections</span></span>  
 [<span data-ttu-id="fa27d-127">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="fa27d-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="fa27d-128">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="fa27d-128">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
 [<span data-ttu-id="fa27d-129">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="fa27d-129">Hosting Services</span></span>](hosting-services.md)  
  
 [<span data-ttu-id="fa27d-130">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="fa27d-130">Building Clients</span></span>](building-clients.md)  
  
 [<span data-ttu-id="fa27d-131">Genişletilebilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa27d-131">Introduction to Extensibility</span></span>](introduction-to-extensibility.md)  
  
 [<span data-ttu-id="fa27d-132">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="fa27d-132">Administration and Diagnostics</span></span>](./diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="fa27d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa27d-133">See also</span></span>

- [<span data-ttu-id="fa27d-134">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="fa27d-134">Basic WCF Programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="fa27d-135">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa27d-135">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="fa27d-136">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="fa27d-136">WCF Feature Details</span></span>](./feature-details/index.md)
