---
title: Özel Güvenli Meta Veri Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 89f12b4490d556884aaa15dcb102b5ad876707ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183843"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="3ebd3-102">Özel Güvenli Meta Veri Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="3ebd3-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="3ebd3-103">Bu örnek, meta olmayan veri değişimi bağlayıcılarından birini kullanan güvenli bir meta veri bitiş noktasına sahip bir hizmetin nasıl uygulanacağını ve [serviceModel Meta data utility aracını (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) veya istemcilerin meta verileri böyle bir meta veri bitiş noktasından nasıl getireceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="3ebd3-104">Meta veri uç noktalarını ortaya çıkarmak için sistem tarafından sağlanan iki bağlama vardır: mexHttpBinding ve mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="3ebd3-105">mexHttpBinding güvenli olmayan bir şekilde HTTP üzerinde bir meta veri bitiş noktası ortaya çıkarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="3ebd3-106">mexHttpsBinding güvenli bir şekilde HTTPS üzerinde bir meta veri bitiş noktası ortaya çıkarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="3ebd3-107">Bu örnek, güvenli bir meta veri bitiş <xref:System.ServiceModel.WSHttpBinding>noktasının nasıl ortaya çıkarılabildiğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="3ebd3-108">Bağlamadaki güvenlik ayarlarını değiştirmek istediğinizde bunu yapmak istersiniz, ancak HTTPS'yi kullanmak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="3ebd3-109">mexHttpsBinding kullanırsanız meta veri bitiş noktanız güvenli olacaktır, ancak bağlama ayarlarını değiştirmenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ebd3-110">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="3ebd3-111">Hizmet</span><span class="sxs-lookup"><span data-stu-id="3ebd3-111">Service</span></span>  
 <span data-ttu-id="3ebd3-112">Bu örnekteki hizmetin iki uç noktası vardır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="3ebd3-113">Uygulama bitiş noktası, `ICalculator` sertifikaları `WSHttpBinding` kullanarak `ReliableSession` etkin `Message` leştirilmiş ve güvenlikli bir sözleşmeye hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="3ebd3-114">Meta veri bitiş noktası `WSHttpBinding`da kullanır , aynı `ReliableSession`güvenlik ayarları ile ama hiçbir .</span><span class="sxs-lookup"><span data-stu-id="3ebd3-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="3ebd3-115">İşte ilgili yapılandırma:</span><span class="sxs-lookup"><span data-stu-id="3ebd3-115">Here is the relevant configuration:</span></span>  
  
```xml  
<services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="3ebd3-116">Diğer örneklerin çoğunda, meta veri bitiş noktası `mexHttpBinding`varsayılan kullanır , güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="3ebd3-117">Burada meta veriler güvenlik `WSHttpBinding` kullanılarak `Message` güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="3ebd3-118">Meta veri istemcilerinin bu meta verileri alabilmesi için eşleşen bir bağlamayla yapılandırılmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="3ebd3-119">Bu örnek, bu tür iki istemciyi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="3ebd3-120">İlk istemci, meta verileri almak ve tasarım zamanında istemci kodu ve yapılandırma oluşturmak için Svcutil.exe kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="3ebd3-121">Hizmet meta veriler için varsayılan olmayan bir bağlama kullandığından, Svcutil.exe aracının bu bağlamayı kullanarak hizmetten meta verileri alabilmesi için özel olarak yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="3ebd3-122">İkinci istemci, `MetadataResolver` bilinen bir sözleşme için meta verileri dinamik olarak getirmek ve ardından dinamik olarak oluşturulan istemci deki işlemleri çağırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="3ebd3-123">Svcutil istemcisi</span><span class="sxs-lookup"><span data-stu-id="3ebd3-123">Svcutil client</span></span>  
 <span data-ttu-id="3ebd3-124">Bitiş noktanızı `IMetadataExchange` barındırmak için varsayılan bağlamayı kullanırken, Svcutil.exe'yi bu bitiş noktasının adresiyle çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3ebd3-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="3ebd3-125">ve işe yarıyor.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-125">and it works.</span></span> <span data-ttu-id="3ebd3-126">Ancak bu örnekte, sunucu meta verileri barındırmak için varsayılan olmayan bir bitiş noktası kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="3ebd3-127">Yani Svcutil.exe doğru bağlama kullanmak için talimat olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="3ebd3-128">Bu bir Svcutil.exe.config dosyası kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="3ebd3-129">Svcutil.exe.config dosyası normal bir istemci yapılandırma dosyası gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="3ebd3-130">Sadece olağandışı yönleri istemci bitiş noktası adı ve sözleşme vardır:</span><span class="sxs-lookup"><span data-stu-id="3ebd3-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="3ebd3-131">Bitiş noktası adı, meta verilerin barındırıldığı adres düzeninin adı olmalı ve bitiş `IMetadataExchange`noktası sözleşmesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="3ebd3-132">Böylece, Svcutil.exe aşağıdaki gibi bir komut satırı ile çalıştırıldığında:</span><span class="sxs-lookup"><span data-stu-id="3ebd3-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="3ebd3-133">meta veri bitiş noktası ile iletişim `IMetadataExchange` alışverişinin bağlayıcıve davranışını yapılandırmak için "http" adlı bitiş noktasını ve sözleşmeyi arar.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="3ebd3-134">Örnekteki Svcutil.exe.config dosyasının geri kalanı, sunucunun meta veri bitiş noktası yapılandırmasına uyacak bağlama yapılandırmasını ve davranış kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="3ebd3-135">Svcutil.exe'nin yapılandırmayı alabilmesi için Svcutil.exe,Svcutil.exe'nin yapılandırma dosyasıyla aynı dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="3ebd3-136">Sonuç olarak, Svcutil.exe'yi yükleme konumundan Svcutil.exe.config dosyasını içeren dizine kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="3ebd3-137">Daha sonra bu dizinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3ebd3-137">Then from that directory, run the following command:</span></span>  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="3ebd3-138">Önde gelen ". \\" bu dizindeki Svcutil.exe'nin (karşılık gelen Svcutil.exe.config' e sahip olan) kopyasının çalıştırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="3ebd3-139">MetadataResolver istemcisi</span><span class="sxs-lookup"><span data-stu-id="3ebd3-139">MetadataResolver client</span></span>  
 <span data-ttu-id="3ebd3-140">İstemci sözleşmeyi biliyorsa ve tasarım zamanında meta verilerle nasıl konuşulabileceğini biliyorsa, istemci uygulama bitiş noktalarının bağlamasını ve adresini dinamik olarak '' `MetadataResolver`kullanarak .</span><span class="sxs-lookup"><span data-stu-id="3ebd3-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="3ebd3-141">Bu örnek istemci, `MetadataResolver` bir `MetadataExchangeClient`.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="3ebd3-142">Svcutil.exe.config'de yer alan aynı bağlama ve sertifika bilgileri `MetadataExchangeClient`zorunlu olarak şu şekilde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="3ebd3-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="3ebd3-143">`mexClient` Yapılandırıldığında, ilgilendiğimiz sözleşmeleri sayısalolarak listeleyebilir ve bu `MetadataResolver` sözleşmelerle ilgili uç noktaların listesini almak için kullanabiliriz:</span><span class="sxs-lookup"><span data-stu-id="3ebd3-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="3ebd3-144">Son olarak, uygulama bitiş noktalarıyla iletişim kurmak için kanallar `ChannelFactory` oluşturmak için kullanılan bir kanalın bağlama ve adresini başlatmayı sağlamak için bu uç noktalardaki bilgileri kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="3ebd3-145">Bu örnek istemcinin temel noktası, kullanıyorsanız `MetadataResolver`ve meta veri değişimi iletişimi için özel bağlamalar veya davranışlar belirtmeniz gerekiyorsa, bu özel ayarları belirtmek için bir `MetadataExchangeClient` kullanabilirsiniz göstermektir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="3ebd3-146">Örneği ayarlamak ve oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3ebd3-146">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="3ebd3-147">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3ebd3-148">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="3ebd3-149">Numuneyi aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3ebd3-149">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="3ebd3-150">Setup.bat'ı örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="3ebd3-151">Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="3ebd3-152">Setup.bat [Windows İletişim Temel Örnekleri için Bir Kerelik Kurulum Yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)setupCertTool.bat çalıştırarak yüklenir FindPrivateKey.exe aracı, kullanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3ebd3-153">İstemci uygulamasını \MetadataResolverClient\bin veya \SvcutilClient\bin'den çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="3ebd3-154">İstemci etkinliği istemci konsoluygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-154">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="3ebd3-155">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-155">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="3ebd3-156">Örneği bitirdikten sonra Cleanup.bat çalıştırarak sertifikaları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="3ebd3-157">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="3ebd3-158">Numuneyi makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3ebd3-158">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="3ebd3-159">Sunucuda, çalıştırın. `setup.bat service`</span><span class="sxs-lookup"><span data-stu-id="3ebd3-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="3ebd3-160">Bağımsız değişkenle birlikte çalışmak, `setup.bat` makinenin tam nitelikli alan adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`</span><span class="sxs-lookup"><span data-stu-id="3ebd3-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="3ebd3-161">Sunucuda, yeni sertifika adını yansıtacak şekilde Web.config'i düzenlemeyi edin.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="3ebd3-162">Diğer bir deyişle, `findValue` [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesindeki özniteliği makinenin tam nitelikli etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="3ebd3-163">Service.cer dosyasını servis dizininden istemci makinesindeki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="3ebd3-164">İstemci üzerinde, çalıştırın. `setup.bat client`</span><span class="sxs-lookup"><span data-stu-id="3ebd3-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="3ebd3-165">Bağımsız değişkenle birlikte çalışmak, `setup.bat` Client.com adında bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarın. `client`</span><span class="sxs-lookup"><span data-stu-id="3ebd3-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="3ebd3-166">İstemci makinesinin `MetadataResolverClient` App.config dosyasında, mex bitiş noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="3ebd3-167">Bunu, localhost'u sunucunun tam nitelikli etki alanı adı ile değiştirerek yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="3ebd3-168">Ayrıca, metadataResolverClient.cs dosyasındaki "localhost" oluşumunu yeni hizmet sertifikası adı (sunucunun tam nitelikli etki alanı adı) olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="3ebd3-169">Aynı şeyi SvcutilClient projesinin App.config'i için de yapın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="3ebd3-170">Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="3ebd3-171">İstemci üzerinde, çalıştırın. `ImportServiceCert.bat`</span><span class="sxs-lookup"><span data-stu-id="3ebd3-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="3ebd3-172">Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="3ebd3-173">Sunucuda, çalıştır `ImportClientCert.bat`, Bu LocalMachine istemci.cer dosyasından istemci sertifikası ilerler - Trusted People deposu.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="3ebd3-174">Servis makinesinde, Visual Studio'da servis projesini oluşturun ve çalıştığını doğrulamak için bir web tarayıcısındayardım sayfasını seçin.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="3ebd3-175">İstemci makinesinde, VS'den MetadataResolverClient'ı veya SvcutilClient'ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="3ebd3-176">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-176">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="3ebd3-177">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="3ebd3-177">To clean up after the sample</span></span>  
  
- <span data-ttu-id="3ebd3-178">Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3ebd3-179">Bu komut dosyası, bu örneği makineler arasında çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="3ebd3-180">Makineler arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="3ebd3-181">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="3ebd3-182">Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3ebd3-183">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3ebd3-184">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-184">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3ebd3-185">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3ebd3-186">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-186">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
