---
title: 'Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: c47539e0c614992efd74296171034b8091ba3f15
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183327"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="1dc7f-102">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1dc7f-102">How to: Secure a Service with Windows Credentials</span></span>
<span data-ttu-id="1dc7f-103">Bu konuda, bir Windows etki alanında bulunan ve aynı etki alanında istemcileri tarafından çağrılan bir Windows Communication Foundation (WCF) hizmeti aktarım güvenliği etkinleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="1dc7f-104">Bu senaryo hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulama ile Aktarım güvenliği](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="1dc7f-105">Örnek bir uygulama için bkz: [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
 <span data-ttu-id="1dc7f-106">Bu konu, mevcut bir sözleşme arabirimi varsa ve uygulama zaten tanımlanmış ve açın ekleyen varsayar.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="1dc7f-107">Bir mevcut hizmet ve istemci de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-107">You can also modify an existing service and client.</span></span>  
  
 <span data-ttu-id="1dc7f-108">Kod içinde tamamen Windows kimlik bilgileri ile bir hizmeti güvenli hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="1dc7f-109">Alternatif olarak, bazı kodları bir yapılandırma dosyası kullanarak atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="1dc7f-110">Bu konu, her iki yönde gösterir.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-110">This topic shows both ways.</span></span> <span data-ttu-id="1dc7f-111">Yalnızca şekilde ikisini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-111">Be sure you only use one of the ways, not both.</span></span>  
  
 <span data-ttu-id="1dc7f-112">İlk üç yordamlar kod kullanarak hizmet güvenliğinin nasıl sağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="1dc7f-113">Dördüncü ve beşinci yordamı, bir yapılandırma dosyası ile nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>  
  
## <a name="using-code"></a><span data-ttu-id="1dc7f-114">Kod kullanarak</span><span class="sxs-lookup"><span data-stu-id="1dc7f-114">Using Code</span></span>  
 <span data-ttu-id="1dc7f-115">Tam hizmet ve istemci için bu konunun sonundaki örneği bölümündeki kodudur.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>  
  
 <span data-ttu-id="1dc7f-116">İlk yordam oluşturma ve yapılandırma aracılığıyla size yol gösterir bir <xref:System.ServiceModel.WSHttpBinding> kod sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="1dc7f-117">Bağlama HTTP aktarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="1dc7f-118">Aynı bağlama istemci üzerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-118">The same binding is used on the client.</span></span>  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="1dc7f-119">İleti güvenliği Windows kimlik bilgilerini kullanan bir WSHttpBinding oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1dc7f-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>  
  
1.  <span data-ttu-id="1dc7f-120">Bu yordamın kod başında eklenen `Run` yöntemi `Test` örnek bölümünde hizmeti kodunda bir sınıfta.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>  
  
2.  <span data-ttu-id="1dc7f-121">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
3.  <span data-ttu-id="1dc7f-122">Ayarlama <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliği <xref:System.ServiceModel.WSHttpSecurity> sınıfının <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
4.  <span data-ttu-id="1dc7f-123">Ayarlama <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.MessageSecurityOverHttp> sınıfının <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>  
  
5.  <span data-ttu-id="1dc7f-124">Bu yordamı için kod aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1dc7f-124">The code for this procedure is as follows:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="1dc7f-125">Bir hizmet olarak bağlama işlemini kullanma</span><span class="sxs-lookup"><span data-stu-id="1dc7f-125">Using the Binding in a Service</span></span>  
 <span data-ttu-id="1dc7f-126">Şirket içinde barındırılan hizmetinde bağlama işlemi gösterilmektedir ikinci yordam budur.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="1dc7f-127">Barındırma hizmetleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="1dc7f-128">Hizmet bağlamayı kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1dc7f-128">To use a binding in a service</span></span>  
  
1.  <span data-ttu-id="1dc7f-129">Bu yordamın kod, önceki yordamdaki koddan sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-129">Insert this procedure's code after the code from the preceding procedure.</span></span>  
  
2.  <span data-ttu-id="1dc7f-130">Oluşturma bir <xref:System.Type> adlı değişken `contractType` ve arabirim türü atayın (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="1dc7f-131">Visual Basic, kullanırken `GetType` işleci; C#, kullanım kullanırken `typeof` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>  
  
3.  <span data-ttu-id="1dc7f-132">Bir saniye oluşturun `Type` adlı değişken `serviceType` ve uygulanan sözleşme türü atayın (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-132">Create a second `Type` variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>  
  
4.  <span data-ttu-id="1dc7f-133">Bir örneğini oluşturmak <xref:System.Uri> adlı sınıfı `baseAddress` hizmetin taban adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="1dc7f-134">Taban adresi taşıma eşleşen bir düzen olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="1dc7f-135">Bu durumda, HTTP taşıma şeması olduğunda ve özel adresini içeren "Localhost" Tekdüzen Kaynak Tanımlayıcısı (URI) ve bağlantı noktası numarası (8036) yanı sıra bir taban uç nokta adresi ("serviceModelSamples /): `http://localhost:8036/serviceModelSamples/`.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>  
  
5.  <span data-ttu-id="1dc7f-136">Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfıyla `serviceType` ve `baseAddress` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>  
  
6.  <span data-ttu-id="1dc7f-137">Kullanarak hizmet için uç nokta ekleme `contractType`, bağlama ve bir uç nokta adı (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="1dc7f-138">Bir istemci taban adresini ve bitiş noktası adı hizmeti çağrısı başlatırken bağlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>  
  
7.  <span data-ttu-id="1dc7f-139">Çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> hizmeti başlatmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="1dc7f-140">Bu yordam kodu aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1dc7f-140">The code for this procedure is shown here:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="1dc7f-141">Bir istemci kullanarak bağlama</span><span class="sxs-lookup"><span data-stu-id="1dc7f-141">Using the Binding in a Client</span></span>  
 <span data-ttu-id="1dc7f-142">Bu yordam, hizmet ile iletişim kuran bir proxy oluşturma adımları anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="1dc7f-143">Proxy ile oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy oluşturmak için hizmet meta verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>  
  
 <span data-ttu-id="1dc7f-144">Bu yordam, ayrıca bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> hizmetiyle iletişim kurmak için sınıf ve ardından hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>  
  
 <span data-ttu-id="1dc7f-145">Bu örnek yalnızca kod istemcisi oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-145">This example uses only code to create the client.</span></span> <span data-ttu-id="1dc7f-146">Alternatif olarak, bu yordamı aşağıdaki bölümde görüntülenen bir yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="1dc7f-147">Bir istemci koduna sahip bir bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1dc7f-147">To use a binding in a client with code</span></span>  
  
1.  <span data-ttu-id="1dc7f-148">Hizmet meta verilerinden proxy kodunu üretmek için SvcUtil.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="1dc7f-149">Daha fazla bilgi için [nasıl yapılır: istemci oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="1dc7f-150">Oluşturulan proxy kodu devraldığı <xref:System.ServiceModel.ClientBase%601> her istemci gerekli Oluşturucular, yöntemleri ve özellikleri bir WCF Hizmeti ile iletişim kurmak için sahip olmasını sağlar sınıfını.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="1dc7f-151">Bu örnekte, oluşturulan kod içeren `CalculatorClient` sınıfını `ICalculator` arabirimi, hizmet kod uyumluluğunu etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>  
  
2.  <span data-ttu-id="1dc7f-152">Bu yordamın kod başında eklenen `Main` istemci programı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
3.  <span data-ttu-id="1dc7f-153">Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama `Message` ve kimlik bilgisi türü için istemci `Windows`.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="1dc7f-154">Örnekte, değişken adları `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-154">The example names the variable `clientBinding`.</span></span>  
  
4.  <span data-ttu-id="1dc7f-155">Bir örneğini oluşturmak <xref:System.ServiceModel.EndpointAddress> adlı sınıfı `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="1dc7f-156">Uç nokta adı ile birleştirilmiş temel adresine sahip örneği başlatır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>  
  
5.  <span data-ttu-id="1dc7f-157">Oluşturulmuş istemci sınıfı örneğini oluşturmak `serviceAddress` ve `clientBinding` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>  
  
6.  <span data-ttu-id="1dc7f-158">Çağrı <xref:System.ServiceModel.ClientBase%601.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
7.  <span data-ttu-id="1dc7f-159">Hizmet çağrısı ve sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-159">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a><span data-ttu-id="1dc7f-160">Yapılandırma dosyasını kullanma</span><span class="sxs-lookup"><span data-stu-id="1dc7f-160">Using the Configuration File</span></span>  
 <span data-ttu-id="1dc7f-161">Yordam kodu ile bağlama oluşturmak yerine, yapılandırma dosyasının bağlamalar bölümü için gösterilen aşağıdaki kodu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>  
  
 <span data-ttu-id="1dc7f-162">Tanımlı bir hizmet zaten yoksa bkz [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md), ve [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
 <span data-ttu-id="1dc7f-163">**Not** bu yapılandırma kod hizmet ve istemci yapılandırma dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-163">**Note** This configuration code is used in both the service and client configuration files.</span></span>  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="1dc7f-164">Aktarım Güvenlik Yapılandırması'nı kullanarak bir Windows etki alanında bir hizmet üzerinde etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="1dc7f-164">To enable transfer security on a service in a Windows domain using configuration</span></span>  
  
1.  <span data-ttu-id="1dc7f-165">Ekleme bir [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesine [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası bölümünü öğesi.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="1dc7f-166">Ekleyin bir <`binding`> öğesi <`WSHttpBinding`> öğesi ve set `configurationName` uygulamanız için uygun bir değer özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>  
  
3.  <span data-ttu-id="1dc7f-167">Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliği ileti.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>  
  
4.  <span data-ttu-id="1dc7f-168">Ekleme bir <`message`> öğesi ve set `clientCredentialType` Windows için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>  
  
5.  <span data-ttu-id="1dc7f-169">Hizmet yapılandırma dosyasında değiştirin `<bindings>` bölümü aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="1dc7f-170">Hizmet yapılandırma dosyasını zaten yoksa bkz [hizmetlerini yapılandırın ve istemciler için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
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
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="1dc7f-171">Bir istemci kullanarak bağlama</span><span class="sxs-lookup"><span data-stu-id="1dc7f-171">Using the Binding in a Client</span></span>  
 <span data-ttu-id="1dc7f-172">Bu yordamda, iki dosya oluşturmak gösterilmiştir: bir proxy hizmeti ve yapılandırma dosyası ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="1dc7f-173">Ayrıca, istemcide kullanılan üçüncü dosya istemci programı değişiklikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-173">It also describes changes to the client program, which is the third file used on the client.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="1dc7f-174">Bir istemci yapılandırma ile bir bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1dc7f-174">To use a binding in a client with configuration</span></span>  
  
1.  <span data-ttu-id="1dc7f-175">Hizmet meta verilerinden proxy kod ve yapılandırma dosyası üretmek için SvcUtil.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="1dc7f-176">Daha fazla bilgi için [nasıl yapılır: istemci oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="1dc7f-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="1dc7f-177">Değiştirin [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) ise önceki bölümden yapılandırma kod ile oluşturulan yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>  
  
3.  <span data-ttu-id="1dc7f-178">Yordam kodu başında eklenen `Main` istemci programı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
4.  <span data-ttu-id="1dc7f-179">Giriş parametresi olarak yapılandırma dosyasında bağlama adını geçirerek oluşturulan istemci sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>  
  
5.  <span data-ttu-id="1dc7f-180">Çağrı <xref:System.ServiceModel.ClientBase%601.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
6.  <span data-ttu-id="1dc7f-181">Hizmet çağrısı ve sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-181">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="1dc7f-182">Örnek</span><span class="sxs-lookup"><span data-stu-id="1dc7f-182">Example</span></span>  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a><span data-ttu-id="1dc7f-183">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1dc7f-183">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 [<span data-ttu-id="1dc7f-184">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1dc7f-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="1dc7f-185">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1dc7f-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="1dc7f-186">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1dc7f-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="1dc7f-187">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1dc7f-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
