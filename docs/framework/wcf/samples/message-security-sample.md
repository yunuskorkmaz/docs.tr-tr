---
title: İleti Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 43e1a9104bdd44509d86bd198559c5e7477a9964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183526"
---
# <a name="message-security-sample"></a><span data-ttu-id="75033-102">İleti Güvenliği Örneği</span><span class="sxs-lookup"><span data-stu-id="75033-102">Message Security Sample</span></span>
<span data-ttu-id="75033-103">Bu örnek, ileti güvenliğini kullanan bir `basicHttpBinding` uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75033-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="75033-104">Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır.</span><span class="sxs-lookup"><span data-stu-id="75033-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75033-105">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="75033-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="75033-106">Güvenlik `basicHttpBinding` modu aşağıdaki değerlere ayarlanabilir: `Message`, `Transport` `TransportWithMessageCredential`, `TransportCredentialOnly` `None`ve .</span><span class="sxs-lookup"><span data-stu-id="75033-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="75033-107">Aşağıdaki örnek hizmet App.config dosyasında, uç nokta `basicHttpBinding` tanımı aşağıdaki örnek `Binding1`yapılandırmada gösterildiği gibi, aşağıdaki örnek yapılandırmada gösterildiği gibi, bağlayıcı bir yapılandırmayı belirtir ve başvurur:</span><span class="sxs-lookup"><span data-stu-id="75033-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="75033-108">Bağlama yapılandırması, `mode` [ \<>güvenlik](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) özniteliğini ayarlar `Message` ve aşağıdaki örnek `Certificate` yapılandırmada gösterildiği gibi [ \<>iletin](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) özniteliğini ayarlar: `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="75033-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="75033-109">Hizmetin kendisini istemciye doğrulamak için kullandığı sertifika, `serviceCredentials` öğenin altındaki yapılandırma dosyasının davranışlar bölümünde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="75033-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="75033-110">İstemcinin kendisini hizmete doğrulamak için kullandığı sertifikaya uygulanan doğrulama modu, öğenin `clientCertificate` altındaki davranışlar bölümünde de ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="75033-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="75033-111">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="75033-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="75033-112">Arayanın kimliği aşağıdaki kod kullanılarak servis konsolu penceresinde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="75033-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="75033-113">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="75033-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="75033-114">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="75033-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="75033-115">Örneği ayarlamak ve oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="75033-115">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="75033-116">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="75033-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="75033-117">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="75033-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="75033-118">Numuneyi aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="75033-118">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="75033-119">Setup.bat'ı örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75033-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="75033-120">Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="75033-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="75033-121">Setup.bat toplu dosyası, Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="75033-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="75033-122">MSSDK ortamı değişkeninin SDK'nın yüklendiği dizine işaret etmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="75033-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="75033-123">Bu ortam değişkeni otomatik olarak bir Windows SDK Komut İstemi içinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="75033-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2. <span data-ttu-id="75033-124">\service\bin'den hizmet uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75033-124">Run the service application from \service\bin.</span></span>  
  
3. <span data-ttu-id="75033-125">İstemci uygulamasını \client\bin'den çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75033-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="75033-126">İstemci etkinliği istemci konsoluygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="75033-126">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="75033-127">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="75033-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5. <span data-ttu-id="75033-128">Örneği bitirdikten sonra Cleanup.bat çalıştırarak sertifikaları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="75033-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="75033-129">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="75033-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="75033-130">Numuneyi makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="75033-130">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="75033-131">Servis ikilileri için servis makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="75033-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="75033-132">Hizmet programı dosyalarını sunucudaki servis dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75033-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="75033-133">Ayrıca Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını sunucuya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75033-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3. <span data-ttu-id="75033-134">İstemci ikilileri için istemci makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="75033-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="75033-135">İstemci programı dosyalarını istemci makinesindeki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75033-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="75033-136">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75033-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="75033-137">Sunucuda, çalıştırın. `setup.bat service`</span><span class="sxs-lookup"><span data-stu-id="75033-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="75033-138">Bağımsız değişkenle birlikte çalışmak, `setup.bat` makinenin tam nitelikli alan adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`</span><span class="sxs-lookup"><span data-stu-id="75033-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="75033-139">Makinenin tam nitelikli alan adı ile aynı olan yeni `findValue` sertifika adını [ \<(serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) öğesindeki öznitelikte) yansıtacak şekilde Service.exe.config'i edin.</span><span class="sxs-lookup"><span data-stu-id="75033-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="75033-140">Ayrıca, localhost yerine tam nitelikli bir makine adı belirtmek için temel adresin değerini değiştirin`.`</span><span class="sxs-lookup"><span data-stu-id="75033-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7. <span data-ttu-id="75033-141">Service.cer dosyasını servis dizininden istemci makinesindeki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75033-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="75033-142">İstemci üzerinde, çalıştırın. `setup.bat client`</span><span class="sxs-lookup"><span data-stu-id="75033-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="75033-143">Bağımsız değişkenle birlikte çalışmak, `setup.bat` client.com adında bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarın. `client`</span><span class="sxs-lookup"><span data-stu-id="75033-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="75033-144">İstemci makinesindeki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="75033-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="75033-145">Bunu, localhost'u sunucunun tam nitelikli etki alanı adı ile değiştirerek yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="75033-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="75033-146">Ayrıca `findValue` [ \<varsayılan Sertifika>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) özniteliğini sunucunun tam nitelikli alan adı olan yeni hizmet sertifikası adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="75033-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="75033-147">Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75033-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="75033-148">İstemci üzerinde ImportServiceCert.bat'ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75033-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="75033-149">Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="75033-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="75033-150">Sunucuda, ImportClientCert.bat çalıştırın, Bu LocalMachine istemci.cer dosyasından istemci sertifikası ilerler - Trusted People deposu.</span><span class="sxs-lookup"><span data-stu-id="75033-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="75033-151">Servis makinesinde Service.exe'yi komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75033-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="75033-152">İstemci makinesinde, istemci.exe komut istemi penceresinden başlatın.</span><span class="sxs-lookup"><span data-stu-id="75033-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1. <span data-ttu-id="75033-153">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="75033-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="75033-154">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="75033-154">To clean up after the sample</span></span>  
  
- <span data-ttu-id="75033-155">Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75033-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="75033-156">Bu komut dosyası, bu örneği makineler arasında çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="75033-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="75033-157">Makineler arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="75033-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="75033-158">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="75033-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="75033-159">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="75033-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="75033-160">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="75033-160">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="75033-161">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="75033-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75033-162">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="75033-162">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
