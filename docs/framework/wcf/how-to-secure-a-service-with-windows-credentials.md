---
title: 'Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
caps.latest.revision: 26
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: c754a4ec57751b2ca5a809c771b2fb5235ec0510
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="54a28-102">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="54a28-102">How to: Secure a Service with Windows Credentials</span></span>
<span data-ttu-id="54a28-103">Bu konu, taşıma güvenliği etkinleştirmek gösterilmiştir bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] bir Windows etki alanında bulunan ve aynı etki alanındaki istemciler tarafından çağrılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="54a28-103">This topic shows how to enable transport security on a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service that resides in a Windows domain and is called by clients in the same domain.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="54a28-104"> Bu senaryo, bkz: [Windows kimlik doğrulama ile taşıma güvenliği](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="54a28-104"> this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="54a28-105">Örnek bir uygulama için bkz: [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="54a28-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
 <span data-ttu-id="54a28-106">Bu konu, varolan sözleşme arabirimi varsa ve uygulama zaten tanımlanmış ve açın ekleyen varsayar.</span><span class="sxs-lookup"><span data-stu-id="54a28-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="54a28-107">Varolan hizmet ve istemci de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54a28-107">You can also modify an existing service and client.</span></span>  
  
 <span data-ttu-id="54a28-108">Windows kimlik bilgilerini tamamen kod hizmetiyle güvenliğini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54a28-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="54a28-109">Alternatif olarak, bazı kodları bir yapılandırma dosyası kullanarak atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54a28-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="54a28-110">Bu konu, her iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54a28-110">This topic shows both ways.</span></span> <span data-ttu-id="54a28-111">Yalnızca bir yolla ikisini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="54a28-111">Be sure you only use one of the ways, not both.</span></span>  
  
 <span data-ttu-id="54a28-112">İlk üç yordamlar kod kullanarak hizmet güvenliğini sağlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="54a28-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="54a28-113">Dördüncü ve beşinci yordam bir yapılandırma dosyası ile nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="54a28-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>  
  
## <a name="using-code"></a><span data-ttu-id="54a28-114">Kod kullanarak</span><span class="sxs-lookup"><span data-stu-id="54a28-114">Using Code</span></span>  
 <span data-ttu-id="54a28-115">Tam hizmeti ve istemci için örnek bölümünde, bu konunun sonunda kodudur.</span><span class="sxs-lookup"><span data-stu-id="54a28-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>  
  
 <span data-ttu-id="54a28-116">İlk yordam oluşturma ve yapılandırma yoluyla anlatılmaktadır bir <xref:System.ServiceModel.WSHttpBinding> kodda sınıfı.</span><span class="sxs-lookup"><span data-stu-id="54a28-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="54a28-117">Bağlama HTTP aktarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="54a28-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="54a28-118">Aynı bağlama istemcide kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54a28-118">The same binding is used on the client.</span></span>  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="54a28-119">Windows kimlik bilgileri ve ileti güvenliği kullanan bir WSHttpBinding oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="54a28-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>  
  
1.  <span data-ttu-id="54a28-120">Bu yordamın kodu başında eklenir `Run` yöntemi `Test` örnek bölümüne hizmet kodunda sınıfta.</span><span class="sxs-lookup"><span data-stu-id="54a28-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>  
  
2.  <span data-ttu-id="54a28-121">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="54a28-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
3.  <span data-ttu-id="54a28-122">Ayarlama <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliği <xref:System.ServiceModel.WSHttpSecurity> sınıfının <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="54a28-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
4.  <span data-ttu-id="54a28-123">Ayarlama <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.MessageSecurityOverHttp> sınıfının <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="54a28-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>  
  
5.  <span data-ttu-id="54a28-124">Bu yordam için kod aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="54a28-124">The code for this procedure is as follows:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="54a28-125">Bir hizmet olarak bağlama işlemini kullanma</span><span class="sxs-lookup"><span data-stu-id="54a28-125">Using the Binding in a Service</span></span>  
 <span data-ttu-id="54a28-126">Bir kendi kendini barındıran hizmet bağlama kullanmayı gösterir ikinci yordam budur.</span><span class="sxs-lookup"><span data-stu-id="54a28-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="54a28-127"> barındırma Hizmetleri Bkz: [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="54a28-127"> hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="54a28-128">Bir hizmet olarak bir bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="54a28-128">To use a binding in a service</span></span>  
  
1.  <span data-ttu-id="54a28-129">Yukarıdaki yordamı koddan sonra bu yordamın kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54a28-129">Insert this procedure's code after the code from the preceding procedure.</span></span>  
  
2.  <span data-ttu-id="54a28-130">Oluşturma bir <xref:System.Type> adlı değişken `contractType` ve arabirim atamak (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="54a28-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="54a28-131">Visual Basic, kullanırken `GetType` C#, kullanım kullanırken işleci; `typeof` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="54a28-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>  
  
3.  <span data-ttu-id="54a28-132">İkinci bir oluşturma `Type` adlı değişken `serviceType` ve uygulanan sözleşme atamak (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="54a28-132">Create a second `Type` variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>  
  
4.  <span data-ttu-id="54a28-133">Bir örneğini oluşturmak <xref:System.Uri> adlı sınıf `baseAddress` hizmetin taban adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="54a28-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="54a28-134">Temel adres taşıma eşleşen bir düzeni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54a28-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="54a28-135">Bu durumda, aktarma düzeni HTTP ve özel adres içerir Tekdüzen Kaynak Tanımlayıcısı (URI) "localhost" ve bir bağlantı noktası numarası (8036) yanı sıra temel uç noktası adresi ("serviceModelSamples /): http://localhost:8036/serviceModelSamples/.</span><span class="sxs-lookup"><span data-stu-id="54a28-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): http://localhost:8036/serviceModelSamples/.</span></span>  
  
5.  <span data-ttu-id="54a28-136">Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> ile sınıf `serviceType` ve `baseAddress` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="54a28-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>  
  
6.  <span data-ttu-id="54a28-137">Hizmeti kullanmaya bir uç nokta ekleyin `contractType`, bağlama ve bir uç nokta adı (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="54a28-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="54a28-138">Bir istemci taban adresini ve uç nokta adı hizmetine yapılan bir çağrı başlatırken birleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="54a28-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>  
  
7.  <span data-ttu-id="54a28-139">Çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> hizmetini başlatmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="54a28-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="54a28-140">Bu yordam için kod aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="54a28-140">The code for this procedure is shown here:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="54a28-141">Bir istemcinin, bağlama kullanma</span><span class="sxs-lookup"><span data-stu-id="54a28-141">Using the Binding in a Client</span></span>  
 <span data-ttu-id="54a28-142">Bu yordam hizmeti ile iletişim kuran bir proxy oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="54a28-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="54a28-143">Proxy ile oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy oluşturmak için hizmet meta verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="54a28-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>  
  
 <span data-ttu-id="54a28-144">Bu yordam, ayrıca bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> hizmetiyle iletişim kurmak için sınıf ve hizmetini çağırır.</span><span class="sxs-lookup"><span data-stu-id="54a28-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>  
  
 <span data-ttu-id="54a28-145">Bu örnek yalnızca kod istemci oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="54a28-145">This example uses only code to create the client.</span></span> <span data-ttu-id="54a28-146">Alternatif olarak, aşağıdaki yordamı bölümünde gösterilen bir yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54a28-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="54a28-147">Kod ile bir istemci bir bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="54a28-147">To use a binding in a client with code</span></span>  
  
1.  <span data-ttu-id="54a28-148">Hizmet meta verilerinden proxy kodu oluşturmak için SvcUtil.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="54a28-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="54a28-149">Daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="54a28-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="54a28-150">Oluşturulan proxy kodu devraldığı <xref:System.ServiceModel.ClientBase%601> her istemci gerekli Oluşturucular, yöntemleri ve özellikleri ile iletişim kurmak için sahip olmasını sağlar sınıfı bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="54a28-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="54a28-151">Bu örnekte, oluşturulan kod içeren `CalculatorClient` sınıfı, hangi uygular `ICalculator` servis kodunu uyumluluğunu etkinleştirme arabirimi.</span><span class="sxs-lookup"><span data-stu-id="54a28-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>  
  
2.  <span data-ttu-id="54a28-152">Bu yordamın kodu başında eklenir `Main` istemci programı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54a28-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
3.  <span data-ttu-id="54a28-153">Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama `Message` ve türü için kimlik bilgisi kendi istemci `Windows`.</span><span class="sxs-lookup"><span data-stu-id="54a28-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="54a28-154">Örnek değişken adları `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="54a28-154">The example names the variable `clientBinding`.</span></span>  
  
4.  <span data-ttu-id="54a28-155">Bir örneğini oluşturmak <xref:System.ServiceModel.EndpointAddress> adlı sınıf `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="54a28-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="54a28-156">Uç nokta adı ile birleştirilmiş taban adresi ile örneği başlatır.</span><span class="sxs-lookup"><span data-stu-id="54a28-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>  
  
5.  <span data-ttu-id="54a28-157">İle oluşturulan istemci sınıfının bir örneği oluşturma `serviceAddress` ve `clientBinding` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="54a28-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>  
  
6.  <span data-ttu-id="54a28-158">Çağrı <xref:System.ServiceModel.ClientBase%601.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54a28-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
7.  <span data-ttu-id="54a28-159">Hizmetini çağırmak ve sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="54a28-159">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a><span data-ttu-id="54a28-160">Yapılandırma dosyasını kullanma</span><span class="sxs-lookup"><span data-stu-id="54a28-160">Using the Configuration File</span></span>  
 <span data-ttu-id="54a28-161">Yordam kodu ile bağlama oluşturmak yerine, yapılandırma dosyasının bağlamaları bölümü için gösterilen aşağıdaki kodu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54a28-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>  
  
 <span data-ttu-id="54a28-162">Tanımlı bir hizmet zaten yoksa bkz [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md), ve [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="54a28-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
 <span data-ttu-id="54a28-163">**Not** bu yapılandırma kodunu hem hizmet hem de istemci yapılandırma dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54a28-163">**Note** This configuration code is used in both the service and client configuration files.</span></span>  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="54a28-164">Bir hizmet yapılandırması'nı kullanarak bir Windows etki alanındaki aktarımı güvenliği etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="54a28-164">To enable transfer security on a service in a Windows domain using configuration</span></span>  
  
1.  <span data-ttu-id="54a28-165">Ekleme bir [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesine [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası öğesi bölümü.</span><span class="sxs-lookup"><span data-stu-id="54a28-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="54a28-166">Ekleme bir <`binding`> öğesi <`WSHttpBinding`> öğesi ve kümesi `configurationName` özniteliği uygulamanız için uygun bir değere.</span><span class="sxs-lookup"><span data-stu-id="54a28-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>  
  
3.  <span data-ttu-id="54a28-167">Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliği ileti.</span><span class="sxs-lookup"><span data-stu-id="54a28-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>  
  
4.  <span data-ttu-id="54a28-168">Ekleme bir <`message`> öğesi ve kümesi `clientCredentialType` özniteliği Windows.</span><span class="sxs-lookup"><span data-stu-id="54a28-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>  
  
5.  <span data-ttu-id="54a28-169">Hizmet yapılandırma dosyasında değiştirin `<bindings>` bölümü aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="54a28-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="54a28-170">Hizmet yapılandırma dosyası zaten yoksa bkz [kullanarak bağlamaları yapılandırma hizmetler ve istemcileri için](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="54a28-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="54a28-171">Bir istemcinin, bağlama kullanma</span><span class="sxs-lookup"><span data-stu-id="54a28-171">Using the Binding in a Client</span></span>  
 <span data-ttu-id="54a28-172">Bu yordamda, iki dosyaları oluşturmak gösterilmiştir: hizmet ve bir yapılandırma dosyası ile iletişim kuran bir proxy.</span><span class="sxs-lookup"><span data-stu-id="54a28-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="54a28-173">Ayrıca, istemcide kullanılan üçüncü dosyası istemci programı değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="54a28-173">It also describes changes to the client program, which is the third file used on the client.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="54a28-174">Bir istemci yapılandırmasına sahip bir bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="54a28-174">To use a binding in a client with configuration</span></span>  
  
1.  <span data-ttu-id="54a28-175">Hizmet meta verilerinden proxy kod ve yapılandırma dosyası oluşturmak için SvcUtil.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="54a28-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="54a28-176">Daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="54a28-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="54a28-177">Değiştir [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) önceki bölümdeki yapılandırma koduyla üretilen yapılandırma dosyasının bölümü.</span><span class="sxs-lookup"><span data-stu-id="54a28-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>  
  
3.  <span data-ttu-id="54a28-178">Yordam kodu başında eklenen `Main` istemci programı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54a28-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
4.  <span data-ttu-id="54a28-179">Giriş parametresi olarak yapılandırma dosyasında bağlama adını geçirerek oluşturulan istemci sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54a28-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>  
  
5.  <span data-ttu-id="54a28-180">Çağrı <xref:System.ServiceModel.ClientBase%601.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54a28-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
6.  <span data-ttu-id="54a28-181">Hizmetini çağırmak ve sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="54a28-181">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="54a28-182">Örnek</span><span class="sxs-lookup"><span data-stu-id="54a28-182">Example</span></span>  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a><span data-ttu-id="54a28-183">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54a28-183">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 [<span data-ttu-id="54a28-184">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="54a28-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="54a28-185">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54a28-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="54a28-186">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="54a28-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="54a28-187">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="54a28-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
