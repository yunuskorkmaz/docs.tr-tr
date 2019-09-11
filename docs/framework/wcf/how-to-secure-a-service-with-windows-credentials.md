---
title: 'Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 19ac9da94ce6e405632293a7d569698c9d866bef
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856056"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="fe60d-102">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fe60d-102">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="fe60d-103">Bu konu başlığı altında, bir Windows etki alanında bulunan ve aynı etki alanındaki istemciler tarafından çağrılan bir Windows Communication Foundation (WCF) hizmetinde aktarım güvenliğinin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="fe60d-104">Bu senaryo hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasıyla taşıma güvenliği](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fe60d-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="fe60d-105">Örnek bir uygulama için bkz. [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="fe60d-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="fe60d-106">Bu konu başlığı altında, var olan bir sözleşme arabirimi ve uygulamanızın zaten tanımlanmış olduğu varsayılır ve bu uygulamaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="fe60d-107">Ayrıca var olan bir hizmeti ve istemciyi de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe60d-107">You can also modify an existing service and client.</span></span>

<span data-ttu-id="fe60d-108">Windows kimlik bilgileriyle bir hizmetin güvenliğini tamamen kodda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe60d-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="fe60d-109">Alternatif olarak, bir yapılandırma dosyası kullanarak bazı kodları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe60d-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="fe60d-110">Bu konuda her iki yol da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-110">This topic shows both ways.</span></span> <span data-ttu-id="fe60d-111">Her ikisini değil yalnızca birini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fe60d-111">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="fe60d-112">İlk üç yordam, kodu kullanarak hizmetin nasıl güvence altına alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="fe60d-113">Dördüncü ve beşinci yordam, bir yapılandırma dosyası ile nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="fe60d-114">Kod kullanma</span><span class="sxs-lookup"><span data-stu-id="fe60d-114">Using Code</span></span>

<span data-ttu-id="fe60d-115">Hizmetin ve istemcinin tüm kodu, bu konunun sonundaki örnek bölümdür.</span><span class="sxs-lookup"><span data-stu-id="fe60d-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="fe60d-116">İlk yordam kodda bir <xref:System.ServiceModel.WSHttpBinding> sınıf oluşturma ve yapılandırmayı adım adım göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="fe60d-117">Bağlama HTTP aktarımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="fe60d-118">İstemcide aynı bağlama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-118">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="fe60d-119">Windows kimlik bilgileri ve ileti güvenliği kullanan bir WSHttpBinding oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fe60d-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="fe60d-120">Bu yordamın kodu, örnek bölümünde hizmet kodundaki `Run` `Test` sınıfının yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="fe60d-121">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe60d-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="fe60d-122">Sınıfının özelliğini olarak<xref:System.ServiceModel.SecurityMode.Message>ayarlayın. <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> <xref:System.ServiceModel.WSHttpSecurity></span><span class="sxs-lookup"><span data-stu-id="fe60d-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="fe60d-123">Sınıfının özelliğini olarak<xref:System.ServiceModel.MessageCredentialType.Windows>ayarlayın. <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> <xref:System.ServiceModel.MessageSecurityOverHttp></span><span class="sxs-lookup"><span data-stu-id="fe60d-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="fe60d-124">Bu yordamın kodu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fe60d-124">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="fe60d-125">Bir hizmette bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="fe60d-125">Using the Binding in a Service</span></span>

<span data-ttu-id="fe60d-126">Bu, bağlamanın şirket içinde barındırılan bir hizmette nasıl kullanılacağını gösteren ikinci yordamdır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="fe60d-127">Barındırma hizmetleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="fe60d-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="fe60d-128">Bir hizmette bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fe60d-128">To use a binding in a service</span></span>

1. <span data-ttu-id="fe60d-129">Önceki yordamdan koddan sonra bu yordamın kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fe60d-129">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="fe60d-130">`ICalculator`Adlı <xref:System.Type> birdeğişkenoluşturunvearabirimintürünü`contractType` () atayın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="fe60d-131">Visual Basic kullanırken `GetType` işlecini kullanın; kullanırken C#, `typeof` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="fe60d-132">`Calculator`Adlı <xref:System.Type> ikincibirdeğişkenoluşturunveuygulanansözleşmenintürünü`serviceType` () atayın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-132">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="fe60d-133">Hizmetin temel adresiyle adlı <xref:System.Uri> `baseAddress` sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fe60d-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="fe60d-134">Temel adres, aktarımdan eşleşen bir şemaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="fe60d-135">Bu durumda, aktarım düzeni HTTP olur ve adres, özel Tekdüzen Kaynak tanımlayıcısı (URI) "localhost" ve bir bağlantı noktası numarası (8036) ve bir taban bitiş noktası adresi ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`ile birlikte yer alır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="fe60d-136">Ve`serviceType` <xref:System.ServiceModel.ServiceHost> değişkenleriilesınıfının`baseAddress` bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fe60d-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="fe60d-137">`contractType`, Bağlamayı ve bir uç nokta adını (secureCalculator) kullanarak hizmete bir uç nokta ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fe60d-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="fe60d-138">Bir istemcinin, hizmete bir çağrı başlatırken temel adresi ve uç nokta adını birleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="fe60d-139">Hizmeti başlatmak için yöntemini çağırın. <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A></span><span class="sxs-lookup"><span data-stu-id="fe60d-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="fe60d-140">Bu yordamın kodu burada gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="fe60d-140">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="fe60d-141">Bir Istemcide bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="fe60d-141">Using the Binding in a Client</span></span>

<span data-ttu-id="fe60d-142">Bu yordamda hizmeti ile iletişim kuran bir proxy oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="fe60d-143">Proxy, proxy 'yi oluşturmak için hizmet meta verilerini kullanan [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe60d-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="fe60d-144">Bu yordam Ayrıca, hizmet ile iletişim kurmak <xref:System.ServiceModel.WSHttpBinding> için sınıfının bir örneğini oluşturur ve ardından hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="fe60d-145">Bu örnek, yalnızca istemciyi oluşturmak için kod kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-145">This example uses only code to create the client.</span></span> <span data-ttu-id="fe60d-146">Alternatif olarak, bu yordamı izleyen bölümünde gösterilen bir yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe60d-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="fe60d-147">Bir istemcide kodla bir bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fe60d-147">To use a binding in a client with code</span></span>

1. <span data-ttu-id="fe60d-148">Hizmetin meta verilerinden proxy kodunu oluşturmak için SvcUtil. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="fe60d-149">Daha fazla bilgi için [nasıl yapılır: Istemci](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fe60d-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="fe60d-150">Oluşturulan proxy kodu <xref:System.ServiceModel.ClientBase%601> sınıfından devralır, bu, her istemcinin bir WCF hizmetiyle iletişim kurmak için gerekli oluşturucular, Yöntemler ve özelliklere sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe60d-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="fe60d-151">Bu örnekte, oluşturulan kod, `CalculatorClient` `ICalculator` arabirimi uygulayan sınıfı içerir ve hizmet koduyla uyumluluğu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="fe60d-152">Bu yordamın kodu, istemci programı `Main` yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="fe60d-153"><xref:System.ServiceModel.WSHttpBinding> Sınıfının bir örneğini oluşturun ve güvenlik `Message` modunu ve onun istemci kimlik bilgisi türünü olarak `Windows`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="fe60d-154">Örnek, değişkenini `clientBinding`adlandırır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-154">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="fe60d-155"><xref:System.ServiceModel.EndpointAddress> Adlı`serviceAddress`sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fe60d-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="fe60d-156">Uç nokta adıyla birleştirilmiş temel adresi olan örneği başlatın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="fe60d-157">Oluşturulan istemci sınıfının `serviceAddress` `clientBinding` ve değişkenlerini içeren bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fe60d-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="fe60d-158">Aşağıdaki kodda gösterildiği gibi yönteminiçağırın.<xref:System.ServiceModel.ClientBase%601.Open%2A></span><span class="sxs-lookup"><span data-stu-id="fe60d-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="fe60d-159">Hizmeti çağırın ve sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="fe60d-159">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="fe60d-160">Yapılandırma dosyasını kullanma</span><span class="sxs-lookup"><span data-stu-id="fe60d-160">Using the Configuration File</span></span>

<span data-ttu-id="fe60d-161">Yordam kodu ile bağlama oluşturmak yerine, yapılandırma dosyasının bağlamalar bölümü için gösterilen aşağıdaki kodu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe60d-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="fe60d-162">Önceden tanımlanmış bir hizmetiniz yoksa, bkz. [Hizmetleri tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md)ve [Hizmetleri yapılandırma](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="fe60d-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fe60d-163">Bu yapılandırma kodu hem hizmet hem de istemci yapılandırma dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe60d-163">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="fe60d-164">Yapılandırma kullanarak Windows etki alanındaki bir hizmette aktarım güvenliğini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="fe60d-164">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="fe60d-165">Yapılandırma [dosyasının \<bağlamalar >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi bölümüne bir [ \<WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fe60d-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="fe60d-166"><`binding``WSHttpBinding` >Öğesinebir<>öğesiekleyinveözniteliğiuygulamanızauygun`configurationName` bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="fe60d-167">Bir <`security`> öğesi ekleyin ve `mode` özniteliği ileti olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="fe60d-168"><`message`Bir > öğesi ekleyin ve `clientCredentialType` özniteliği Windows 'a ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="fe60d-169">Hizmetin yapılandırma dosyasında `<bindings>` bölümünü aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fe60d-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="fe60d-170">Zaten bir hizmet yapılandırma dosyanız yoksa, bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fe60d-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>

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

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="fe60d-171">Bir Istemcide bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="fe60d-171">Using the Binding in a Client</span></span>

<span data-ttu-id="fe60d-172">Bu yordamda iki dosyanın nasıl oluşturulacağı gösterilmektedir: hizmetle iletişim kuran bir ara sunucu ve bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="fe60d-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="fe60d-173">Ayrıca, istemci programında, istemcide kullanılan üçüncü dosya olan değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe60d-173">It also describes changes to the client program, which is the third file used on the client.</span></span>

##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="fe60d-174">Yapılandırmaya sahip bir istemcide bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fe60d-174">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="fe60d-175">Proxy kodunu ve yapılandırma dosyasını hizmetin meta verilerinden oluşturmak için SvcUtil. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe60d-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="fe60d-176">Daha fazla bilgi için [nasıl yapılır: Istemci](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fe60d-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="fe60d-177">Oluşturulan yapılandırma dosyasının [ bağlama>bölümünü,öncekibölümdekiyapılandırmakoduiledeğiştirin.\<](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="fe60d-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="fe60d-178">Yordam kodu, istemci programı `Main` yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="fe60d-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="fe60d-179">Yapılandırma dosyasındaki bağlamanın adını giriş parametresi olarak geçirerek oluşturulan istemci sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fe60d-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="fe60d-180">Aşağıdaki kodda gösterildiği gibi yönteminiçağırın.<xref:System.ServiceModel.ClientBase%601.Open%2A></span><span class="sxs-lookup"><span data-stu-id="fe60d-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="fe60d-181">Hizmeti çağırın ve sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="fe60d-181">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="fe60d-182">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe60d-182">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="fe60d-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe60d-183">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="fe60d-184">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="fe60d-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="fe60d-185">Nasıl yapılır: Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe60d-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="fe60d-186">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fe60d-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="fe60d-187">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fe60d-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
