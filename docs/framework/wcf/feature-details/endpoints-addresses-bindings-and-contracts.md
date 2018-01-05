---
title: "Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af82cb934570b371d332c0e08ebc9b2338d0c0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="bd8bd-102">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="bd8bd-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="bd8bd-103">İle tüm iletişimin bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] servis oluşur aracılığıyla *uç noktaları* hizmetinin.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-103">All communication with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="bd8bd-104">Uç noktaları tarafından sunulan işlevselliği erişim istemcileri sağlar bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-104">Endpoints provide clients access to the functionality offered by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="bd8bd-105">Her uç nokta dört özelliklerini oluşur:</span><span class="sxs-lookup"><span data-stu-id="bd8bd-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="bd8bd-106">Uç nokta bulunabileceği gösteren bir adres.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="bd8bd-107">Bir bağlama istemci uç noktasıyla nasıl iletişim kurabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="bd8bd-108">Kullanılabilir işlemleri tanımlayan bir sözleşme.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="bd8bd-109">Yerel uygulama uç nokta ayrıntılarını belirtin davranışları kümesi.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="bd8bd-110">Bu konu Bu uç nokta yapısını açıklar ve nasıl içinde gösterilir açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-110">This topic discusses this endpoint structure and explains how it is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="bd8bd-111">Bir uç nokta yapısı</span><span class="sxs-lookup"><span data-stu-id="bd8bd-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="bd8bd-112">Her uç nokta aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="bd8bd-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="bd8bd-113">Adresi: Adresi benzersiz olarak uç noktayı tanımlar ve olası söyler bulunduğu olduğu hizmet tüketicileri.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="bd8bd-114">' De temsil [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nesne modeli tarafından <xref:System.ServiceModel.EndpointAddress> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-114">It is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="bd8bd-115">Bir <xref:System.ServiceModel.EndpointAddress> sınıfı içerir:</span><span class="sxs-lookup"><span data-stu-id="bd8bd-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="bd8bd-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> hizmetinin adresini gösteren özelliği.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="bd8bd-117">Bir <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliği hizmet güvenlik kimliğini ve isteğe bağlı bir ileti üstbilgileri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="bd8bd-118">Daha ayrıntılı tanımlamak veya uç noktasıyla etkileşim için adresleme bilgi ve isteğe bağlı ileti üstbilgilerini ek sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="bd8bd-119">[Bir uç noktası adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="bd8bd-119"> [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="bd8bd-120">Bağlama: Bağlama bitiş noktası ile iletişim kurmak nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="bd8bd-121">Şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="bd8bd-121">This includes:</span></span>  
  
    -   <span data-ttu-id="bd8bd-122">(Örneğin, TCP veya HTTP) kullanmak için Aktarım Protokolü.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="bd8bd-123">(Örneğin, metin veya ikili) iletileri için kullanılacak kodlama.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="bd8bd-124">Gerekli güvenlik gereksinimleri (örneğin, SSL veya SOAP iletisi güvenlik).</span><span class="sxs-lookup"><span data-stu-id="bd8bd-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="bd8bd-125">[WCF bağlamaları genel bakış](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd8bd-125"> [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="bd8bd-126">İçinde bir bağlaması temsil [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nesne modeli Özet temel sınıf tarafından <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-126">A binding is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="bd8bd-127">Çoğu senaryoda, kullanıcılar sistem tarafından sağlanan bağlamalar birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="bd8bd-128">Daha fazla bilgi için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="bd8bd-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="bd8bd-129">Sözleşmeleri: Sözleşme istemciye uç noktasını kullanıma sunar hangi işlevsellikler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="bd8bd-130">Bir sözleşme belirtir:</span><span class="sxs-lookup"><span data-stu-id="bd8bd-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="bd8bd-131">Hangi işlemlerin bir istemci tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="bd8bd-132">İleti biçimi.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="bd8bd-133">Giriş parametreleri veya çağrı işlemi için gereken veri türü.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="bd8bd-134">Ne tür bir işlem veya yanıt iletisi istemci bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="bd8bd-135">Bir sözleşme tanımlama hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="bd8bd-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="bd8bd-136">Davranışları: Hizmet uç noktası yerel davranışını özelleştirmek için uç nokta davranışları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="bd8bd-137">Uç nokta davranışları elde bu oluşturma sürecinde katılarak bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-137">Endpoint behaviors achieve this by participating in the process of building a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]runtime.</span></span> <span data-ttu-id="bd8bd-138">Bir uç noktası davranışı örneği <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> SOAP ve Web Hizmetleri Açıklama Dili (WSDL) adresinden farklı bir dinleme adresi belirtmenize olanak tanır özelliği.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="bd8bd-139">[ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="bd8bd-139"> [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="bd8bd-140">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="bd8bd-140">Defining Endpoints</span></span>  
 <span data-ttu-id="bd8bd-141">Uç nokta ya da imperatively kod kullanarak bir hizmet için veya yapılandırma yoluyla bildirimli olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="bd8bd-142">[Nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) ve [nasıl yapılır: kod içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="bd8bd-142"> [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd8bd-143">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bd8bd-143">In This Section</span></span>  
 <span data-ttu-id="bd8bd-144">Bu bölümde bağlamaları, uç noktaları ve adresleri amacını açıklayan; bağlama ve bir uç nokta nasıl yapılandırılacağını gösterir; ve nasıl kullanılacağını göstermektedir `ClientVia` davranışı ve `ListenUri` özelliği.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="bd8bd-145">Adresler</span><span class="sxs-lookup"><span data-stu-id="bd8bd-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="bd8bd-146">Uç noktaları nasıl değinilen açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd8bd-146">Describes how endpoints are addressed in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="bd8bd-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bd8bd-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="bd8bd-148">Taşıma, kodlama ve istemcileri ve Hizmetleri birbirleri ile iletişim kurması gereken protokol ayrıntılarını belirtmek için bağlamaları nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="bd8bd-149">Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="bd8bd-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="bd8bd-150">Sözleşmeler yöntemleri bir hizmetin nasıl tanımlar açıklar.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="bd8bd-151">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bd8bd-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="bd8bd-152">Hizmet uç noktası yapılandırmasında oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="bd8bd-153">Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bd8bd-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="bd8bd-154">Kod içinde hizmet uç noktası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="bd8bd-155">Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma</span><span class="sxs-lookup"><span data-stu-id="bd8bd-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="bd8bd-156">Hata hizmet uygulamaları ve yapılandırmaları kullanarak hizmet barındırma olmadan algılamaya açıklar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bd8bd-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8bd-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd8bd-157">See Also</span></span>  
 [<span data-ttu-id="bd8bd-158">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bd8bd-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="bd8bd-159">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="bd8bd-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
