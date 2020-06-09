---
title: 'Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593522"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="88505-102">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="88505-102">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="88505-103">Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur.</span><span class="sxs-lookup"><span data-stu-id="88505-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="88505-104">Uç noktalar, istemcilere bir WCF hizmeti tarafından sunulan işlevlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="88505-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="88505-105">Her uç nokta dört özelliklerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="88505-105">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="88505-106">Uç noktanın nerede bulunamayacağını gösteren bir adres.</span><span class="sxs-lookup"><span data-stu-id="88505-106">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="88505-107">Bir istemcinin bitiş noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="88505-107">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="88505-108">Kullanılabilir işlemleri tanımlayan bir anlaşma.</span><span class="sxs-lookup"><span data-stu-id="88505-108">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="88505-109">Uç noktanın yerel uygulama ayrıntılarını belirten davranışlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="88505-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="88505-110">Bu konu, bu uç nokta yapısını tartışır ve WCF nesne modelinde nasıl temsil edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="88505-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="88505-111">Bir uç noktanın yapısı</span><span class="sxs-lookup"><span data-stu-id="88505-111">The Structure of an Endpoint</span></span>

<span data-ttu-id="88505-112">Her uç nokta aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="88505-112">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="88505-113">Adres: adres, uç noktayı benzersiz bir şekilde tanımlar ve hizmetin bulunduğu tüketicilere ait potansiyel tüketicilere bildirir.</span><span class="sxs-lookup"><span data-stu-id="88505-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="88505-114">Sınıfı tarafından WCF nesne modelinde temsil edilir <xref:System.ServiceModel.EndpointAddress> .</span><span class="sxs-lookup"><span data-stu-id="88505-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="88505-115">Bir <xref:System.ServiceModel.EndpointAddress> sınıf şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="88505-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="88505-116"><xref:System.ServiceModel.EndpointAddress.Uri%2A>Hizmetin adresini temsil eden bir özellik.</span><span class="sxs-lookup"><span data-stu-id="88505-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="88505-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A>Hizmetin güvenlik kimliğini ve isteğe bağlı ileti üstbilgileri koleksiyonunu temsil eden bir özellik.</span><span class="sxs-lookup"><span data-stu-id="88505-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="88505-118">İsteğe bağlı ileti üstbilgileri, uç noktayı tanımlamak veya bunlarla etkileşime geçmek üzere ek ve daha ayrıntılı adresleme bilgileri sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88505-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="88505-119">Daha fazla bilgi için bkz. [uç nokta adresi belirtme](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="88505-119">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="88505-120">Bağlama: bağlama, bitiş noktasıyla nasıl iletişim kuracağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="88505-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="88505-121">Buna aşağıdakiler dahildir:</span><span class="sxs-lookup"><span data-stu-id="88505-121">This includes:</span></span>

  - <span data-ttu-id="88505-122">Kullanılacak Aktarım Protokolü (örneğin, TCP veya HTTP).</span><span class="sxs-lookup"><span data-stu-id="88505-122">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="88505-123">İletiler için kullanılacak kodlama (örneğin, metin veya ikili).</span><span class="sxs-lookup"><span data-stu-id="88505-123">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="88505-124">Gerekli güvenlik gereksinimleri (örneğin, SSL veya SOAP iletisi güvenliği).</span><span class="sxs-lookup"><span data-stu-id="88505-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="88505-125">Daha fazla bilgi için bkz. [WCF bağlamalarına genel bakış](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="88505-125">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="88505-126">Bir bağlama, WCF nesne modelinde soyut temel sınıf tarafından temsil edilir <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="88505-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="88505-127">Çoğu senaryoda, kullanıcılar sistem tarafından belirtilen bağlamalardan birini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="88505-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="88505-128">Daha fazla bilgi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="88505-128">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="88505-129">Sözleşmeler: sözleşme, uç noktanın istemciye sunduğu işlevleri özetler.</span><span class="sxs-lookup"><span data-stu-id="88505-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="88505-130">Bir sözleşme şunları belirtir:</span><span class="sxs-lookup"><span data-stu-id="88505-130">A contract specifies:</span></span>

  - <span data-ttu-id="88505-131">İstemci tarafından hangi işlemleri çağrılabilecek.</span><span class="sxs-lookup"><span data-stu-id="88505-131">What operations can be called by a client.</span></span>

  - <span data-ttu-id="88505-132">İleti formu.</span><span class="sxs-lookup"><span data-stu-id="88505-132">The form of the message.</span></span>

  - <span data-ttu-id="88505-133">İşlemi çağırmak için gereken giriş parametrelerinin veya verilerin türü.</span><span class="sxs-lookup"><span data-stu-id="88505-133">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="88505-134">İstemcinin tahmin edebilecekleri işlem veya yanıt iletisi türü.</span><span class="sxs-lookup"><span data-stu-id="88505-134">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="88505-135">Sözleşme tanımlama hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="88505-135">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="88505-136">Davranışlar: uç nokta davranışlarını, hizmet uç noktasının yerel davranışını özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88505-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="88505-137">Endpoint davranışları, WCF çalışma zamanı oluşturma işlemine katılarak bunu elde etmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="88505-137">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="88505-138">Bir uç nokta davranışı örneği <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> , soap veya Web Hizmetleri Açıklama Dili (wsdl) adresinden farklı bir dinleme adresi belirtmenizi sağlayan özelliktir.</span><span class="sxs-lookup"><span data-stu-id="88505-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="88505-139">Daha fazla bilgi için bkz. [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="88505-139">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="88505-140">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="88505-140">Defining Endpoints</span></span>

<span data-ttu-id="88505-141">Bir hizmet için uç noktayı kod kullanarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88505-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="88505-142">Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-configuration.md) ve [nasıl yapılır: kod Içinde hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="88505-142">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="88505-143">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="88505-143">In This Section</span></span>

<span data-ttu-id="88505-144">Bu bölümde bağlamalar, uç noktalar ve adreslerin amacı açıklanmaktadır; bir bağlamanın ve uç noktanın nasıl yapılandırılacağını gösterir; ve `ClientVia` davranışın ve özelliğinin nasıl kullanılacağını gösterir `ListenUri` .</span><span class="sxs-lookup"><span data-stu-id="88505-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="88505-145">[Gideren](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="88505-145">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="88505-146">Uç noktaların WCF 'de nasıl giderildiği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88505-146">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="88505-147">[Lara](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="88505-147">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="88505-148">İstemcilerin ve hizmetlerin birbirleriyle iletişim kurması için gereken aktarım, kodlama ve protokol ayrıntılarını belirtmek için bağlamaların nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="88505-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="88505-149">[Sözleşmeleri](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="88505-149">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="88505-150">Sözleşmelerin bir hizmet yöntemlerini nasıl tanımlalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="88505-150">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="88505-151">[Nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="88505-151">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="88505-152">Yapılandırmada bir hizmet uç noktası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="88505-152">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="88505-153">[Nasıl yapılır: kod içinde hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="88505-153">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="88505-154">Kodda bir hizmet uç noktası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="88505-154">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="88505-155">[Nasıl yapılır: derlenmiş hizmet kodunu doğrulamak için Svcutil. exe kullanma](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="88505-155">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="88505-156">Hizmet uygulamalarında ve yapılandırmalarda [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak hizmeti barındırmadan hataların nasıl algılanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="88505-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88505-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88505-157">See also</span></span>

- [<span data-ttu-id="88505-158">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="88505-158">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="88505-159">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="88505-159">Extending Bindings</span></span>](../extending/extending-bindings.md)
