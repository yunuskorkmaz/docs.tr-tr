---
title: 'Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme'
description: Windows etki alanında bulunan ve aynı etki alanındaki istemciler tarafından çağrılan bir WCF hizmetinde aktarım güvenliğini etkinleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 8ef164e1475bfd5f047a99426a2bed43a7aa7353
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244640"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="e27b4-103">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e27b4-103">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="e27b4-104">Bu konu başlığı altında, bir Windows etki alanında bulunan ve aynı etki alanındaki istemciler tarafından çağrılan bir Windows Communication Foundation (WCF) hizmetinde aktarım güvenliğinin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-104">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="e27b4-105">Bu senaryo hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasıyla taşıma güvenliği](./feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e27b4-105">For more information about this scenario, see [Transport Security with Windows Authentication](./feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="e27b4-106">Örnek bir uygulama için bkz. [WSHttpBinding](./samples/wshttpbinding.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="e27b4-106">For a sample application, see the [WSHttpBinding](./samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="e27b4-107">Bu konu başlığı altında, var olan bir sözleşme arabirimi ve uygulamanızın zaten tanımlanmış olduğu varsayılır ve bu uygulamaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-107">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="e27b4-108">Ayrıca var olan bir hizmeti ve istemciyi de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e27b4-108">You can also modify an existing service and client.</span></span>

<span data-ttu-id="e27b4-109">Windows kimlik bilgileriyle bir hizmetin güvenliğini tamamen kodda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e27b4-109">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="e27b4-110">Alternatif olarak, bir yapılandırma dosyası kullanarak bazı kodları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e27b4-110">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="e27b4-111">Bu konuda her iki yol da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-111">This topic shows both ways.</span></span> <span data-ttu-id="e27b4-112">Her ikisini değil yalnızca birini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e27b4-112">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="e27b4-113">İlk üç yordam, kodu kullanarak hizmetin nasıl güvence altına alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-113">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="e27b4-114">Dördüncü ve beşinci yordam, bir yapılandırma dosyası ile nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-114">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="e27b4-115">Kod kullanma</span><span class="sxs-lookup"><span data-stu-id="e27b4-115">Using Code</span></span>

<span data-ttu-id="e27b4-116">Hizmetin ve istemcinin tüm kodu, bu konunun sonundaki örnek bölümdür.</span><span class="sxs-lookup"><span data-stu-id="e27b4-116">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="e27b4-117">İlk yordam kodda bir sınıf oluşturma ve yapılandırmayı adım adım göstermektedir <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="e27b4-117">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="e27b4-118">Bağlama HTTP aktarımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e27b4-118">The binding uses the HTTP transport.</span></span> <span data-ttu-id="e27b4-119">İstemcide aynı bağlama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e27b4-119">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="e27b4-120">Windows kimlik bilgileri ve ileti güvenliği kullanan bir WSHttpBinding oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e27b4-120">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="e27b4-121">Bu yordamın kodu, `Run` `Test` örnek bölümünde hizmet kodundaki sınıfının yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-121">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="e27b4-122">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e27b4-122">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="e27b4-123"><xref:System.ServiceModel.WSHttpSecurity.Mode%2A> <xref:System.ServiceModel.WSHttpSecurity> Sınıfının özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.Message> .</span><span class="sxs-lookup"><span data-stu-id="e27b4-123">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="e27b4-124"><xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> <xref:System.ServiceModel.MessageSecurityOverHttp> Sınıfının özelliğini olarak ayarlayın <xref:System.ServiceModel.MessageCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="e27b4-124">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="e27b4-125">Bu yordamın kodu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e27b4-125">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="e27b4-126">Bir hizmette bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="e27b4-126">Using the Binding in a Service</span></span>

<span data-ttu-id="e27b4-127">Bu, bağlamanın şirket içinde barındırılan bir hizmette nasıl kullanılacağını gösteren ikinci yordamdır.</span><span class="sxs-lookup"><span data-stu-id="e27b4-127">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="e27b4-128">Barındırma hizmetleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="e27b4-128">For more information about hosting services see [Hosting Services](hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="e27b4-129">Bir hizmette bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e27b4-129">To use a binding in a service</span></span>

1. <span data-ttu-id="e27b4-130">Önceki yordamdan koddan sonra bu yordamın kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e27b4-130">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="e27b4-131">Adlı bir <xref:System.Type> değişken oluşturun `contractType` ve arabirimin türünü ( `ICalculator` ) atayın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-131">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="e27b4-132">Visual Basic kullanırken `GetType` işlecini kullanın; C# kullanırken, `typeof` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-132">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="e27b4-133">Adlı ikinci bir <xref:System.Type> değişken oluşturun `serviceType` ve uygulanan sözleşmenin türünü ( `Calculator` ) atayın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-133">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="e27b4-134"><xref:System.Uri>Hizmetin temel adresiyle adlı sınıfının bir örneğini oluşturun `baseAddress` .</span><span class="sxs-lookup"><span data-stu-id="e27b4-134">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="e27b4-135">Temel adres, aktarımdan eşleşen bir şemaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e27b4-135">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="e27b4-136">Bu durumda, aktarım düzeni HTTP olur ve adres, özel Tekdüzen Kaynak tanımlayıcısı (URI) "localhost" ve bir bağlantı noktası numarası (8036) ve bir taban bitiş noktası adresi ("serviceModelSamples/): ile birlikte yer alır `http://localhost:8036/serviceModelSamples/` .</span><span class="sxs-lookup"><span data-stu-id="e27b4-136">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="e27b4-137"><xref:System.ServiceModel.ServiceHost>Ve değişkenleri ile sınıfının bir örneğini oluşturun `serviceType` `baseAddress` .</span><span class="sxs-lookup"><span data-stu-id="e27b4-137">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="e27b4-138">`contractType`, Bağlamayı ve bir uç nokta adını (secureCalculator) kullanarak hizmete bir uç nokta ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e27b4-138">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="e27b4-139">Bir istemcinin, hizmete bir çağrı başlatırken temel adresi ve uç nokta adını birleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-139">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="e27b4-140"><xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>Hizmeti başlatmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-140">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="e27b4-141">Bu yordamın kodu burada gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e27b4-141">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="e27b4-142">Bir Istemcide bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="e27b4-142">Using the Binding in a Client</span></span>

<span data-ttu-id="e27b4-143">Bu yordamda hizmeti ile iletişim kuran bir proxy oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-143">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="e27b4-144">Proxy, proxy 'yi oluşturmak için hizmet meta verilerini kullanan [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e27b4-144">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="e27b4-145">Bu yordam Ayrıca, <xref:System.ServiceModel.WSHttpBinding> hizmet ile iletişim kurmak için sınıfının bir örneğini oluşturur ve ardından hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="e27b4-145">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="e27b4-146">Bu örnek, yalnızca istemciyi oluşturmak için kod kullanır.</span><span class="sxs-lookup"><span data-stu-id="e27b4-146">This example uses only code to create the client.</span></span> <span data-ttu-id="e27b4-147">Alternatif olarak, bu yordamı izleyen bölümünde gösterilen bir yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e27b4-147">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="e27b4-148">Bir istemcide kodla bir bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e27b4-148">To use a binding in a client with code</span></span>

1. <span data-ttu-id="e27b4-149">Hizmetin meta verilerinden proxy kodunu oluşturmak için SvcUtil.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-149">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="e27b4-150">Daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="e27b4-150">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="e27b4-151">Oluşturulan proxy kodu sınıfından devralır, bu <xref:System.ServiceModel.ClientBase%601> , her istemcinin BIR WCF hizmetiyle iletişim kurmak için gerekli oluşturucular, Yöntemler ve özelliklere sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e27b4-151">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="e27b4-152">Bu örnekte, oluşturulan kod, `CalculatorClient` arabirimi uygulayan sınıfı içerir ve `ICalculator` hizmet koduyla uyumluluğu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-152">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="e27b4-153">Bu yordamın kodu, `Main` istemci programı yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-153">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="e27b4-154">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.WSHttpBinding> ve güvenlik modunu `Message` ve onun istemci kimlik bilgisi türünü olarak ayarlayın `Windows` .</span><span class="sxs-lookup"><span data-stu-id="e27b4-154">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="e27b4-155">Örnek, değişkenini adlandırır `clientBinding` .</span><span class="sxs-lookup"><span data-stu-id="e27b4-155">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="e27b4-156">Adlı sınıfının bir örneğini oluşturun <xref:System.ServiceModel.EndpointAddress> `serviceAddress` .</span><span class="sxs-lookup"><span data-stu-id="e27b4-156">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="e27b4-157">Uç nokta adıyla birleştirilmiş temel adresi olan örneği başlatın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-157">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="e27b4-158">Oluşturulan istemci sınıfının ve değişkenlerini içeren bir örneğini oluşturun `serviceAddress` `clientBinding` .</span><span class="sxs-lookup"><span data-stu-id="e27b4-158">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="e27b4-159"><xref:System.ServiceModel.ClientBase%601.Open%2A>Aşağıdaki kodda gösterildiği gibi yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-159">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="e27b4-160">Hizmeti çağırın ve sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="e27b4-160">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="e27b4-161">Yapılandırma dosyasını kullanma</span><span class="sxs-lookup"><span data-stu-id="e27b4-161">Using the Configuration File</span></span>

<span data-ttu-id="e27b4-162">Yordam kodu ile bağlama oluşturmak yerine, yapılandırma dosyasının bağlamalar bölümü için gösterilen aşağıdaki kodu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e27b4-162">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="e27b4-163">Önceden tanımlanmış bir hizmetiniz yoksa, bkz. [Hizmetleri tasarlama ve uygulama](designing-and-implementing-services.md)ve [Hizmetleri yapılandırma](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="e27b4-163">If you do not already have a service defined, see [Designing and Implementing Services](designing-and-implementing-services.md), and [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e27b4-164">Bu yapılandırma kodu hem hizmet hem de istemci yapılandırma dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e27b4-164">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="e27b4-165">Yapılandırma kullanarak Windows etki alanındaki bir hizmette aktarım güvenliğini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="e27b4-165">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="e27b4-166">[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) Yapılandırma dosyasının öğe bölümüne bir öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e27b4-166">Add a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="e27b4-167">`binding`<> öğesine bir <> öğesi ekleyin `WSHttpBinding` ve `configurationName` özniteliği uygulamanıza uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-167">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="e27b4-168">Bir <`security`> öğesi ekleyin ve `mode` özniteliği ileti olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-168">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="e27b4-169"><bir `message`> öğesi ekleyin ve `clientCredentialType` özniteliği Windows 'a ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-169">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="e27b4-170">Hizmetin yapılandırma dosyasında `<bindings>` bölümünü aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e27b4-170">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="e27b4-171">Zaten bir hizmet yapılandırma dosyanız yoksa, bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e27b4-171">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

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

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="e27b4-172">Bir Istemcide bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="e27b4-172">Using the Binding in a Client</span></span>

<span data-ttu-id="e27b4-173">Bu yordamda iki dosyanın nasıl oluşturulacağı gösterilmektedir: hizmetle iletişim kuran bir ara sunucu ve bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="e27b4-173">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="e27b4-174">Ayrıca, istemci programında, istemcide kullanılan üçüncü dosya olan değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e27b4-174">It also describes changes to the client program, which is the third file used on the client.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="e27b4-175">Yapılandırmaya sahip bir istemcide bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e27b4-175">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="e27b4-176">Proxy kodunu ve yapılandırma dosyasını hizmetin meta verilerinden oluşturmak için SvcUtil.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-176">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="e27b4-177">Daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="e27b4-177">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="e27b4-178">[\<bindings>](../configure-apps/file-schema/wcf/bindings.md)Oluşturulan yapılandırma dosyasının bölümünü, önceki bölümdeki yapılandırma kodu ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e27b4-178">Replace the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="e27b4-179">Yordam kodu, `Main` istemci programı yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="e27b4-179">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="e27b4-180">Yapılandırma dosyasındaki bağlamanın adını giriş parametresi olarak geçirerek oluşturulan istemci sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e27b4-180">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="e27b4-181"><xref:System.ServiceModel.ClientBase%601.Open%2A>Aşağıdaki kodda gösterildiği gibi yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e27b4-181">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="e27b4-182">Hizmeti çağırın ve sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="e27b4-182">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="e27b4-183">Örnek</span><span class="sxs-lookup"><span data-stu-id="e27b4-183">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="e27b4-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e27b4-184">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="e27b4-185">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="e27b4-185">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="e27b4-186">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e27b4-186">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="e27b4-187">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e27b4-187">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="e27b4-188">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="e27b4-188">Security Overview</span></span>](./feature-details/security-overview.md)
