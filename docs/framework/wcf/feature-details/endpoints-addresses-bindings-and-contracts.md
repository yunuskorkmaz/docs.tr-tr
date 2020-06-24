---
title: 'Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler'
description: Bir WCF hizmeti ile iletişimin, istemcilere hizmet tarafından sunulan işlevlere erişmesini sağlayan hizmet uç noktaları aracılığıyla nasıl oluştuğunu öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: ce0874bfed716716b6fd1801b35a4266095cd752
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247318"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="8ed26-103">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="8ed26-103">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="8ed26-104">Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur.</span><span class="sxs-lookup"><span data-stu-id="8ed26-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="8ed26-105">Uç noktalar, istemcilere bir WCF hizmeti tarafından sunulan işlevlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ed26-105">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="8ed26-106">Her uç nokta dört özelliklerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="8ed26-106">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="8ed26-107">Uç noktanın nerede bulunamayacağını gösteren bir adres.</span><span class="sxs-lookup"><span data-stu-id="8ed26-107">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="8ed26-108">Bir istemcinin bitiş noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="8ed26-108">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="8ed26-109">Kullanılabilir işlemleri tanımlayan bir anlaşma.</span><span class="sxs-lookup"><span data-stu-id="8ed26-109">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="8ed26-110">Uç noktanın yerel uygulama ayrıntılarını belirten davranışlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="8ed26-110">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="8ed26-111">Bu konu, bu uç nokta yapısını tartışır ve WCF nesne modelinde nasıl temsil edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ed26-111">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="8ed26-112">Bir uç noktanın yapısı</span><span class="sxs-lookup"><span data-stu-id="8ed26-112">The Structure of an Endpoint</span></span>

<span data-ttu-id="8ed26-113">Her uç nokta aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="8ed26-113">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="8ed26-114">Adres: adres, uç noktayı benzersiz bir şekilde tanımlar ve hizmetin bulunduğu tüketicilere ait potansiyel tüketicilere bildirir.</span><span class="sxs-lookup"><span data-stu-id="8ed26-114">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="8ed26-115">Sınıfı tarafından WCF nesne modelinde temsil edilir <xref:System.ServiceModel.EndpointAddress> .</span><span class="sxs-lookup"><span data-stu-id="8ed26-115">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="8ed26-116">Bir <xref:System.ServiceModel.EndpointAddress> sınıf şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="8ed26-116">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="8ed26-117"><xref:System.ServiceModel.EndpointAddress.Uri%2A>Hizmetin adresini temsil eden bir özellik.</span><span class="sxs-lookup"><span data-stu-id="8ed26-117">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="8ed26-118"><xref:System.ServiceModel.EndpointAddress.Identity%2A>Hizmetin güvenlik kimliğini ve isteğe bağlı ileti üstbilgileri koleksiyonunu temsil eden bir özellik.</span><span class="sxs-lookup"><span data-stu-id="8ed26-118">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="8ed26-119">İsteğe bağlı ileti üstbilgileri, uç noktayı tanımlamak veya bunlarla etkileşime geçmek üzere ek ve daha ayrıntılı adresleme bilgileri sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ed26-119">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="8ed26-120">Daha fazla bilgi için bkz. [uç nokta adresi belirtme](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="8ed26-120">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="8ed26-121">Bağlama: bağlama, bitiş noktasıyla nasıl iletişim kuracağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ed26-121">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="8ed26-122">Buna aşağıdakiler dahildir:</span><span class="sxs-lookup"><span data-stu-id="8ed26-122">This includes:</span></span>

  - <span data-ttu-id="8ed26-123">Kullanılacak Aktarım Protokolü (örneğin, TCP veya HTTP).</span><span class="sxs-lookup"><span data-stu-id="8ed26-123">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="8ed26-124">İletiler için kullanılacak kodlama (örneğin, metin veya ikili).</span><span class="sxs-lookup"><span data-stu-id="8ed26-124">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="8ed26-125">Gerekli güvenlik gereksinimleri (örneğin, SSL veya SOAP iletisi güvenliği).</span><span class="sxs-lookup"><span data-stu-id="8ed26-125">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="8ed26-126">Daha fazla bilgi için bkz. [WCF bağlamalarına genel bakış](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8ed26-126">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="8ed26-127">Bir bağlama, WCF nesne modelinde soyut temel sınıf tarafından temsil edilir <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="8ed26-127">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="8ed26-128">Çoğu senaryoda, kullanıcılar sistem tarafından belirtilen bağlamalardan birini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ed26-128">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="8ed26-129">Daha fazla bilgi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="8ed26-129">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="8ed26-130">Sözleşmeler: sözleşme, uç noktanın istemciye sunduğu işlevleri özetler.</span><span class="sxs-lookup"><span data-stu-id="8ed26-130">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="8ed26-131">Bir sözleşme şunları belirtir:</span><span class="sxs-lookup"><span data-stu-id="8ed26-131">A contract specifies:</span></span>

  - <span data-ttu-id="8ed26-132">İstemci tarafından hangi işlemleri çağrılabilecek.</span><span class="sxs-lookup"><span data-stu-id="8ed26-132">What operations can be called by a client.</span></span>

  - <span data-ttu-id="8ed26-133">İleti formu.</span><span class="sxs-lookup"><span data-stu-id="8ed26-133">The form of the message.</span></span>

  - <span data-ttu-id="8ed26-134">İşlemi çağırmak için gereken giriş parametrelerinin veya verilerin türü.</span><span class="sxs-lookup"><span data-stu-id="8ed26-134">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="8ed26-135">İstemcinin tahmin edebilecekleri işlem veya yanıt iletisi türü.</span><span class="sxs-lookup"><span data-stu-id="8ed26-135">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="8ed26-136">Sözleşme tanımlama hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8ed26-136">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="8ed26-137">Davranışlar: uç nokta davranışlarını, hizmet uç noktasının yerel davranışını özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ed26-137">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="8ed26-138">Endpoint davranışları, WCF çalışma zamanı oluşturma işlemine katılarak bunu elde etmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="8ed26-138">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="8ed26-139">Bir uç nokta davranışı örneği <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> , soap veya Web Hizmetleri Açıklama Dili (wsdl) adresinden farklı bir dinleme adresi belirtmenizi sağlayan özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8ed26-139">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="8ed26-140">Daha fazla bilgi için bkz. [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="8ed26-140">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="8ed26-141">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="8ed26-141">Defining Endpoints</span></span>

<span data-ttu-id="8ed26-142">Bir hizmet için uç noktayı kod kullanarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ed26-142">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="8ed26-143">Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-configuration.md) ve [nasıl yapılır: kod Içinde hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="8ed26-143">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8ed26-144">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8ed26-144">In This Section</span></span>

<span data-ttu-id="8ed26-145">Bu bölümde bağlamalar, uç noktalar ve adreslerin amacı açıklanmaktadır; bir bağlamanın ve uç noktanın nasıl yapılandırılacağını gösterir; ve `ClientVia` davranışın ve özelliğinin nasıl kullanılacağını gösterir `ListenUri` .</span><span class="sxs-lookup"><span data-stu-id="8ed26-145">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="8ed26-146">[Gideren](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="8ed26-146">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="8ed26-147">Uç noktaların WCF 'de nasıl giderildiği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ed26-147">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="8ed26-148">[Lara](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8ed26-148">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="8ed26-149">İstemcilerin ve hizmetlerin birbirleriyle iletişim kurması için gereken aktarım, kodlama ve protokol ayrıntılarını belirtmek için bağlamaların nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ed26-149">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="8ed26-150">[Sözleşmeleri](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="8ed26-150">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="8ed26-151">Sözleşmelerin bir hizmet yöntemlerini nasıl tanımlalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ed26-151">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="8ed26-152">[Nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="8ed26-152">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="8ed26-153">Yapılandırmada bir hizmet uç noktası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ed26-153">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="8ed26-154">[Nasıl yapılır: kod içinde hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="8ed26-154">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="8ed26-155">Kodda bir hizmet uç noktası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ed26-155">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="8ed26-156">[Nasıl yapılır: derlenmiş hizmet kodunu doğrulamak için Svcutil.exe kullanma](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="8ed26-156">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="8ed26-157">Hizmet uygulamalarında ve yapılandırmalarda [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak hizmeti barındırmadan hataların nasıl algılanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ed26-157">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ed26-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ed26-158">See also</span></span>

- [<span data-ttu-id="8ed26-159">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8ed26-159">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="8ed26-160">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8ed26-160">Extending Bindings</span></span>](../extending/extending-bindings.md)
