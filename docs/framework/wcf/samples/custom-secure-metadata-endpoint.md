---
title: Özel Güvenli Meta Veri Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 072d2551acaae87904bb12c5e8edafa788674322
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045131"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="fd55a-102">Özel Güvenli Meta Veri Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="fd55a-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="fd55a-103">Bu örnek, meta veri olmayan Exchange bağlamalarından birini kullanan güvenli bir meta veri uç noktası olan bir hizmetin nasıl uygulanacağını ve [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) veya istemcilerin bu tür bir kaynaktan meta verileri getirmek için nasıl yapılandırılacağını gösterir. meta veri uç noktası.</span><span class="sxs-lookup"><span data-stu-id="fd55a-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="fd55a-104">Meta veri uç noktalarını açığa çıkarmak için kullanılabilir iki sistem tarafından sağlanan bağlama vardır: mexHttpBinding ve mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="fd55a-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="fd55a-105">mexHttpBinding, bir meta veri uç noktasının HTTP üzerinden güvenli olmayan bir şekilde kullanıma sunulması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="fd55a-106">mexHttpsBinding, HTTPS üzerinden bir meta veri uç noktası oluşturmak için güvenli bir şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="fd55a-107">Bu örnek, <xref:System.ServiceModel.WSHttpBinding>kullanarak güvenli bir meta veri uç noktasının nasıl açığa alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="fd55a-108">Bağlamasındaki güvenlik ayarlarını değiştirmek istediğinizde, ancak HTTPS kullanmak istemiyorsanız bunu yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd55a-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="fd55a-109">MexHttpsBinding kullanırsanız, meta veri uç noktanız güvende olur, ancak bağlama ayarlarını değiştirmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd55a-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="fd55a-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="fd55a-111">Hizmet</span><span class="sxs-lookup"><span data-stu-id="fd55a-111">Service</span></span>  
 <span data-ttu-id="fd55a-112">Bu örnekteki hizmette iki uç nokta bulunur.</span><span class="sxs-lookup"><span data-stu-id="fd55a-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="fd55a-113">Uygulama uç noktası, sertifikaları `ICalculator` etkin ve `Message` güvenli `WSHttpBinding` bir `ReliableSession` şekilde sertifikalar kullanarak sunar.</span><span class="sxs-lookup"><span data-stu-id="fd55a-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="fd55a-114">Meta veri uç noktası aynı `WSHttpBinding`güvenlik ayarlarıyla ancak Hayır `ReliableSession`ile de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="fd55a-115">İlgili yapılandırma aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fd55a-115">Here is the relevant configuration:</span></span>  
  
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
  
 <span data-ttu-id="fd55a-116">Diğer birçok örnek için, meta veri uç noktası, güvenli olmayan varsayılanı `mexHttpBinding`kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="fd55a-117">Burada meta veriler güvenlik `WSHttpBinding` ile `Message` güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="fd55a-118">Meta veri istemcilerinin bu meta verileri alabilmesi için, eşleşen bir bağlama ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="fd55a-119">Bu örnek, bu iki istemciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="fd55a-120">İlk istemci, meta verileri getirmek ve tasarım zamanında istemci kodu ve yapılandırması oluşturmak için Svcutil. exe ' yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="fd55a-121">Hizmet meta veriler için varsayılan olmayan bir bağlama kullandığından, bu bağlamayı kullanarak hizmetten meta verileri alabilmek için Svcutil. exe aracının özel olarak yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="fd55a-122">İkinci istemci, `MetadataResolver` bilinen bir sözleşmenin meta verilerini dinamik olarak getirmek için öğesini kullanır ve sonra dinamik olarak üretilen istemcideki işlemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="fd55a-123">Svcutil istemcisi</span><span class="sxs-lookup"><span data-stu-id="fd55a-123">Svcutil client</span></span>  
 <span data-ttu-id="fd55a-124">Uç noktanızı `IMetadataExchange` barındırmak için varsayılan bağlamayı kullanırken, Svcutil. exe ' yi bu uç noktanın adresiyle çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fd55a-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="fd55a-125">ve işe yarar.</span><span class="sxs-lookup"><span data-stu-id="fd55a-125">and it works.</span></span> <span data-ttu-id="fd55a-126">Ancak bu örnekte, sunucu meta verileri barındırmak için varsayılan olmayan bir uç nokta kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="fd55a-127">Bu nedenle, doğru bağlamayı kullanması için Svcutil. exe ' ye bir talimat verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="fd55a-128">Bu, bir Svcutil. exe. config dosyası kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="fd55a-129">Svcutil. exe. config dosyası normal bir istemci yapılandırma dosyası gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="fd55a-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="fd55a-130">İstemci uç noktası adı ve sözleşmesinin tek olağandışı yönleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fd55a-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="fd55a-131">Uç nokta adı, meta verilerin barındırıldığı adresin düzeninin adı ve uç nokta sözleşmesinin olması `IMetadataExchange`gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="fd55a-132">Bu nedenle, Svcutil. exe, aşağıdaki gibi bir komut satırı ile çalıştırıldığında:</span><span class="sxs-lookup"><span data-stu-id="fd55a-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="fd55a-133">Bu, "http" adlı uç noktayı ve iletişim değişiminin `IMetadataExchange` bağlama ve davranışını meta veri uç noktasıyla yapılandırmak üzere sözleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="fd55a-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="fd55a-134">Örnekteki Svcutil. exe. config dosyasının geri kalanı, bağlama yapılandırma ve davranış kimlik bilgilerini sunucunun meta veri uç noktası yapılandırmasıyla eşleşecek şekilde belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="fd55a-135">Svcutil. exe, Svcutil. exe. config dosyasındaki yapılandırmayı çekmek için Svcutil. exe ' nin yapılandırma dosyası ile aynı dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="fd55a-136">Sonuç olarak, Svcutil. exe ' yi kendi install konumundan, Svcutil. exe. config dosyasını içeren dizine kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="fd55a-137">Ardından, bu dizinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fd55a-137">Then from that directory, run the following command:</span></span>  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="fd55a-138">Önde gelen ". \\"Bu dizindeki Svcutil. exe kopyasının (karşılık gelen bir Svcutil. exe. config dosyasına sahip olan) çalıştırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd55a-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="fd55a-139">MetadataResolver istemcisi</span><span class="sxs-lookup"><span data-stu-id="fd55a-139">MetadataResolver client</span></span>  
 <span data-ttu-id="fd55a-140">İstemci sözleşmeyi bilir ve tasarım zamanında meta verilerle nasıl iletişim kuracağınızı, istemci, `MetadataResolver`kullanarak uygulama uç noktalarının bağlamasını ve adresini dinamik olarak bulabilir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="fd55a-141">Bu örnek istemci, tarafından kullanılan bağlama ve kimlik bilgilerinin, bir `MetadataResolver` `MetadataExchangeClient`oluşturup yapılandırarak tarafından nasıl yapılandırılacağını gösteren bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="fd55a-142">Svcutil. exe. config dosyasında görünen aynı bağlama ve sertifika bilgileri, `MetadataExchangeClient`imperatively üzerinde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="fd55a-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="fd55a-143">Yapılandırma ile ilgilendiğimiz sözleşmeleri listeleyebilir ve bu sözleşmeleri içeren uç noktalar listesini getirmek için kullanabilirsiniz `MetadataResolver`: `mexClient`</span><span class="sxs-lookup"><span data-stu-id="fd55a-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="fd55a-144">Son olarak, bu uç noktaların bilgilerini, uygulama uç noktalarıyla iletişim kurmak üzere kanal oluşturmak için `ChannelFactory` kullanılan bağlamayı ve adresini başlatmak üzere kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="fd55a-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="fd55a-145">Bu örnek istemcinin anahtar noktası, kullanıyorsanız `MetadataResolver`ve meta veri değişimi iletişimi için özel bağlamalar veya davranışlar belirtmeniz gerekiyorsa, bu özel ayarları belirtmek için bir `MetadataExchangeClient` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd55a-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="fd55a-146">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="fd55a-146">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="fd55a-147">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fd55a-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fd55a-148">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fd55a-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="fd55a-149">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fd55a-149">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="fd55a-150">Örnek yükleme klasöründen Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fd55a-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="fd55a-151">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="fd55a-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="fd55a-152">Setup. bat dosyasının, [Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamından](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)setupCertTool. bat dosyasını çalıştırarak yüklenen FindPrivateKey. exe aracını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fd55a-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fd55a-153">İstemci uygulamasını \MetadataResolverClient\bin veya \SvcutilClient\bin. adresinden çalıştırın</span><span class="sxs-lookup"><span data-stu-id="fd55a-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="fd55a-154">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-154">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="fd55a-155">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="fd55a-155">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="fd55a-156">Örnek ile işiniz bittiğinde Cleanup. bat çalıştırarak sertifikaları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fd55a-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="fd55a-157">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="fd55a-158">Örneği makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fd55a-158">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="fd55a-159">Sunucusunda öğesini çalıştırın `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="fd55a-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="fd55a-160">Bağımsız`service` değişkeniyle birlikte çalıştırmak `setup.bat` makinenin tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="fd55a-161">Sunucusunda, Web. config dosyasını yeni sertifika adını yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="fd55a-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="fd55a-162">Diğer bir deyişle, `findValue` [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesindeki özniteliğini makinenin tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fd55a-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="fd55a-163">Service. cer dosyasını hizmet dizininden istemci makinesindeki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fd55a-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="fd55a-164">İstemcisinde öğesini çalıştırın `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="fd55a-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="fd55a-165">Bağımsız `setup.bat` değişkeniyle birlikte `client` çalıştırmak, Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="fd55a-166">İstemci makinesindeki uygulamasının App. config dosyasında `MetadataResolverClient` , MEX uç noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fd55a-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="fd55a-167">Bunu, localhost yerine sunucunun tam etki alanı adıyla değiştirerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd55a-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="fd55a-168">Ayrıca, metadataResolverClient.cs dosyasındaki "localhost" öğesinin oluşumunu yeni hizmet sertifikası adına (sunucunun tam etki alanı adı) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fd55a-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="fd55a-169">SvcutilClient projesinin App. config ' i için aynı şeyi yapın.</span><span class="sxs-lookup"><span data-stu-id="fd55a-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="fd55a-170">Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fd55a-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="fd55a-171">İstemcisinde öğesini çalıştırın `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="fd55a-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="fd55a-172">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="fd55a-173">Sunucusunda, bu `ImportClientCert.bat`, istemci sertifikasını Client. cer dosyasından LocalMachine-trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="fd55a-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="fd55a-174">Hizmet makinesinde, Visual Studio 'da hizmet projesini derleyin ve çalıştığını doğrulamak için bir Web tarayıcısında yardım sayfasını seçin.</span><span class="sxs-lookup"><span data-stu-id="fd55a-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="fd55a-175">İstemci makinesinde, ve adresinden MetadataResolverClient veya SvcutilClient ' ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fd55a-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="fd55a-176">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="fd55a-176">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="fd55a-177">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="fd55a-177">To clean up after the sample</span></span>  
  
- <span data-ttu-id="fd55a-178">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fd55a-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fd55a-179">Bu betik, makineler arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="fd55a-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="fd55a-180">Makinelerde sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fd55a-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="fd55a-181">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="fd55a-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="fd55a-182">Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="fd55a-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fd55a-183">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd55a-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fd55a-184">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fd55a-184">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="fd55a-185">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="fd55a-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fd55a-186">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fd55a-186">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
