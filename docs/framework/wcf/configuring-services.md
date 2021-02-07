---
description: 'Daha fazla bilgi edinin: WCF hizmetlerini yapılandırma'
title: WCF hizmetlerini yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 1c0df8c7d9b4e2b1a032f02e74db2de4a8de020c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720845"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="02d96-103">WCF hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="02d96-103">Configuring WCF services</span></span>

<span data-ttu-id="02d96-104">Hizmet sözleşmenizi tasarladıktan ve uyguladıktan sonra, hizmetinizi yapılandırmaya hazırlanın.</span><span class="sxs-lookup"><span data-stu-id="02d96-104">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="02d96-105">Burada, hizmetinizin, bulunabileceği adresi belirtme, ileti göndermek ve almak için kullandığı Aktarım ve ileti kodlama ve gerek duyduğu güvenlik türü dahil olmak üzere, istemcilerin istemcilere sunulma şeklini tanımlamanız ve özelleştirmeniz burada yer alır.</span><span class="sxs-lookup"><span data-stu-id="02d96-105">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="02d96-106">Burada kullanılan yapılandırma, bir hizmetin uç nokta adreslerini, kullanılan taşımaları ve güvenlik düzenlerini belirtmek gibi bir hizmetin çeşitli yönlerini tanımlayabileceğiniz ve özelleştirebileceğiniz bir yapılandırma dosyası kullanarak tüm yolları, imperatively içinde veya bir yapılandırma dosyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="02d96-106">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="02d96-107">Uygulamada, yapılandırma yazma, WCF uygulamalarının Programlamanın önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="02d96-107">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="02d96-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="02d96-108">In This Section</span></span>  

 [<span data-ttu-id="02d96-109">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="02d96-109">Simplified Configuration</span></span>](simplified-configuration.md)  
 <span data-ttu-id="02d96-110">WCF, .NET Framework 4 ' te başlayarak WCF yapılandırma gereksinimlerini kolaylaştıran yeni bir varsayılan yapılandırma modeliyle gelir.</span><span class="sxs-lookup"><span data-stu-id="02d96-110">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="02d96-111">Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma zamanı hizmetinizi otomatik olarak varsayılan uç noktalar, bağlamalar ve davranışlar ile yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="02d96-111">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="02d96-112">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="02d96-112">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
 <span data-ttu-id="02d96-113">Windows Communication Foundation (WCF) hizmeti, .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="02d96-113">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="02d96-114">En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran bir Internet Information Services (IIS) sitesi için Web.config dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="02d96-114">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="02d96-115">Öğeler, bir makine temelinde, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="02d96-115">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="02d96-116">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="02d96-116">Bindings</span></span>](bindings.md)  
 <span data-ttu-id="02d96-117">Ayrıca, WCF, istemci ve hizmetin nasıl iletişim kurduğu, aktarımlar, güvenlik ve ileti kodlamaları gibi en temel özellikleri hızlı bir şekilde seçmenizi sağlayan bağlamalar biçiminde sistem tarafından sunulan birçok ortak yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="02d96-117">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="02d96-118">Uç Noktalar</span><span class="sxs-lookup"><span data-stu-id="02d96-118">Endpoints</span></span>](endpoints.md)  
 <span data-ttu-id="02d96-119">WCF hizmeti ile kurulan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur.</span><span class="sxs-lookup"><span data-stu-id="02d96-119">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="02d96-120">Uç noktalar sözleşmeyi, bağlamalarda belirtilen yapılandırma bilgilerini ve hizmetin nerede bulunacağını veya hizmet hakkındaki bilgilerin nerede alınacağını belirten adresleri içerir.</span><span class="sxs-lookup"><span data-stu-id="02d96-120">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="02d96-121">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="02d96-121">Securing Services</span></span>](securing-services.md)  
 <span data-ttu-id="02d96-122">WCF ve mevcut güvenlik mekanizmalarını kullanarak, herhangi bir hizmete gizlilik, bütünlük, kimlik doğrulama ve yetkilendirme uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02d96-122">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="02d96-123">Ayrıca güvenlik başarıları ve başarısızlıklarını da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02d96-123">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="02d96-124">WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02d96-124">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="02d96-125">Diğer platformların veya işletim sistemindeki hizmetler ve istemcilerle birlikte çalışabilen bir hizmeti dağıtmaya yönelik gereksinimler, WS-ı temel profil 1,1 belirtiminde özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="02d96-125">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="02d96-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="02d96-126">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="02d96-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="02d96-127">Related Sections</span></span>  

 [<span data-ttu-id="02d96-128">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="02d96-128">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="02d96-129">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="02d96-129">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
 [<span data-ttu-id="02d96-130">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="02d96-130">Hosting Services</span></span>](hosting-services.md)  
  
 [<span data-ttu-id="02d96-131">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="02d96-131">Building Clients</span></span>](building-clients.md)  
  
 [<span data-ttu-id="02d96-132">Genişletilebilirlik Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="02d96-132">Introduction to Extensibility</span></span>](introduction-to-extensibility.md)  
  
 [<span data-ttu-id="02d96-133">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="02d96-133">Administration and Diagnostics</span></span>](./diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="02d96-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02d96-134">See also</span></span>

- [<span data-ttu-id="02d96-135">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="02d96-135">Basic WCF Programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="02d96-136">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="02d96-136">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="02d96-137">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="02d96-137">WCF Feature Details</span></span>](./feature-details/index.md)
