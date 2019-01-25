---
title: 'Uç noktalar: Adresleri, bağlamalar ve sözleşmeler'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: a10d9ac5718bf6b88a3a00902f90045c705f8431
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721795"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="431e8-102">Uç noktalar: Adresleri, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="431e8-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="431e8-103">Bir Windows Communication Foundation (WCF) hizmetiyle kurulan tüm iletişimlerde üzerinden gerçekleşir *uç noktaları* hizmeti.</span><span class="sxs-lookup"><span data-stu-id="431e8-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="431e8-104">Uç noktaları, istemcilerin bir WCF hizmeti tarafından sunulan işlevlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="431e8-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>  
  
 <span data-ttu-id="431e8-105">Her uç nokta dört özelliklerini oluşur:</span><span class="sxs-lookup"><span data-stu-id="431e8-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="431e8-106">Uç nokta bulunabileceği gösteren bir adres.</span><span class="sxs-lookup"><span data-stu-id="431e8-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="431e8-107">Bir bağlama için bir istemci uç noktasıyla nasıl iletişim kurabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="431e8-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="431e8-108">Kullanılabilir işlemleri tanımlayan bir sözleşme.</span><span class="sxs-lookup"><span data-stu-id="431e8-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="431e8-109">Yerel uygulama uç nokta ayrıntılarını belirtin davranışları kümesi.</span><span class="sxs-lookup"><span data-stu-id="431e8-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="431e8-110">Bu konu, bu uç nokta yapısını açıklar ve WCF nesne modelinde nasıl temsil edildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="431e8-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="431e8-111">Bir uç nokta yapısı</span><span class="sxs-lookup"><span data-stu-id="431e8-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="431e8-112">Her uç nokta aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="431e8-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="431e8-113">Adresi: Adresi benzersiz şekilde uç noktayı tanımlar ve olası söyler, nerede hizmet tüketicileri.</span><span class="sxs-lookup"><span data-stu-id="431e8-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="431e8-114">WCF nesne modeli tarafından temsil edilir <xref:System.ServiceModel.EndpointAddress> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="431e8-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="431e8-115">Bir <xref:System.ServiceModel.EndpointAddress> sınıfı içerir:</span><span class="sxs-lookup"><span data-stu-id="431e8-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="431e8-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> hizmetinin adresini temsil eden özellik.</span><span class="sxs-lookup"><span data-stu-id="431e8-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="431e8-117">Bir <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliği hizmetin güvenlik kimliğini ve isteğe bağlı ileti üstbilgileri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="431e8-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="431e8-118">İsteğe bağlı ileti üstbilgilerini ek sağlamak için kullanılır ve daha ayrıntılı tanımlamak veya uç nokta ile etkileşime geçmek için adresleme bilgi.</span><span class="sxs-lookup"><span data-stu-id="431e8-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     <span data-ttu-id="431e8-119">Daha fazla bilgi için [bir uç nokta adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="431e8-119">For more information, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="431e8-120">Bağlama: Bağlama uç noktasıyla iletişim nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="431e8-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="431e8-121">Şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="431e8-121">This includes:</span></span>  
  
    -   <span data-ttu-id="431e8-122">(Örneğin, TCP veya HTTP) kullanılacak taşıma protokol.</span><span class="sxs-lookup"><span data-stu-id="431e8-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="431e8-123">(Örneğin, metin veya ikili) iletileri için kullanılacak kodlama.</span><span class="sxs-lookup"><span data-stu-id="431e8-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="431e8-124">Gerekli güvenlik gereksinimlerini (örneğin, SSL veya SOAP ileti güvenliği).</span><span class="sxs-lookup"><span data-stu-id="431e8-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     <span data-ttu-id="431e8-125">Daha fazla bilgi için [WCF bağlamaları genel bakış](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="431e8-125">For more information, see [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="431e8-126">Bir bağlama WCF nesne modelinde soyut taban sınıfı tarafından temsil edilen <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="431e8-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="431e8-127">Çoğu senaryo için kullanıcılara sistem tarafından sağlanan bağlamalar birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="431e8-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="431e8-128">Daha fazla bilgi için [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="431e8-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="431e8-129">Sözleşmeler: Sözleşme istemciye uç noktasını kullanıma sunar işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="431e8-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="431e8-130">Bir sözleşme belirtir:</span><span class="sxs-lookup"><span data-stu-id="431e8-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="431e8-131">Hangi işlemleri, bir istemci tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="431e8-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="431e8-132">İleti biçimi.</span><span class="sxs-lookup"><span data-stu-id="431e8-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="431e8-133">Giriş parametreleri veya çağrı işlemi için gerekli veri türü.</span><span class="sxs-lookup"><span data-stu-id="431e8-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="431e8-134">Ne tür bir işlem veya yanıt iletisi, istemci bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="431e8-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="431e8-135">Bir sözleşme tanımlama hakkında daha fazla bilgi için bkz. [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="431e8-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="431e8-136">Davranışlar: Uç nokta davranışları, yerel hizmet uç noktası davranışını özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="431e8-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="431e8-137">Uç nokta davranışları bir WCFruntime oluşturma sürecinde katılarak elde edin.</span><span class="sxs-lookup"><span data-stu-id="431e8-137">Endpoint behaviors achieve this by participating in the process of building a WCFruntime.</span></span> <span data-ttu-id="431e8-138">Bir uç nokta davranışı örneğidir <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> özelliği bir SOAP veya Web Hizmetleri Açıklama Dili (WSDL) adresi dinleme adresinizden farklı belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="431e8-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="431e8-139">Daha fazla bilgi için [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="431e8-139">For more information, see [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="431e8-140">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="431e8-140">Defining Endpoints</span></span>  
 <span data-ttu-id="431e8-141">Uç nokta ya da kesin kod kullanarak bir hizmet için veya yapılandırma yoluyla bildirimli olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="431e8-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="431e8-142">Daha fazla bilgi için [nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) ve [nasıl yapılır: Kod içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="431e8-142">For more information, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="431e8-143">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="431e8-143">In This Section</span></span>  
 <span data-ttu-id="431e8-144">Bu bölümde bağlamaları, uç noktaları ve adres amacını açıklar; bir bağlama ve bir uç nokta nasıl yapılandırılacağını gösterir. ve nasıl kullanılacağını gösteren `ClientVia` davranışı ve `ListenUri` özelliği.</span><span class="sxs-lookup"><span data-stu-id="431e8-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="431e8-145">Adresler</span><span class="sxs-lookup"><span data-stu-id="431e8-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="431e8-146">Uç noktaları WCF'de nasıl ele alınır açıklar.</span><span class="sxs-lookup"><span data-stu-id="431e8-146">Describes how endpoints are addressed in WCF.</span></span>  
  
 [<span data-ttu-id="431e8-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="431e8-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="431e8-148">Aktarım, kodlama ve istemciler ve hizmetler birbirleri ile iletişim kurmak için gerekli Protokolü ayrıntıları belirtmek için bağlamaları nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="431e8-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="431e8-149">Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="431e8-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="431e8-150">Nasıl yöntemlerini hizmet sözleşmelerini tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="431e8-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="431e8-151">Nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="431e8-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="431e8-152">Yapılandırma içinde hizmet uç noktası oluşturma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="431e8-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="431e8-153">Nasıl yapılır: Kod içinde hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="431e8-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="431e8-154">Kod içinde hizmet uç noktası oluşturma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="431e8-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="431e8-155">Nasıl yapılır: Derlenmiş hizmet kodunu doğrulamak için svcutil.exe kullanma</span><span class="sxs-lookup"><span data-stu-id="431e8-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="431e8-156">Hizmetini kullanarak barındırma olmadan hizmet uygulamaları ve yapılandırmalarında hataları algılamak nasıl açıklar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="431e8-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431e8-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="431e8-157">See also</span></span>
- [<span data-ttu-id="431e8-158">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="431e8-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="431e8-159">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="431e8-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
