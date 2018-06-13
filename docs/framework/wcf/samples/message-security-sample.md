---
title: İleti Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0b04dea120a54189dc1738a51d0ea7a842489506
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507244"
---
# <a name="message-security-sample"></a><span data-ttu-id="5188f-102">İleti Güvenliği Örneği</span><span class="sxs-lookup"><span data-stu-id="5188f-102">Message Security Sample</span></span>
<span data-ttu-id="5188f-103">Bu örnek nasıl kullanan bir uygulamayı uygulanacağını gösterilen `basicHttpBinding` ve güvenlik iletisi.</span><span class="sxs-lookup"><span data-stu-id="5188f-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="5188f-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="5188f-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5188f-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="5188f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5188f-106">Güvenlik modunu `basicHttpBinding` aşağıdaki değerleri ayarlayın: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="5188f-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="5188f-107">Aşağıdaki örnek hizmet App.config dosyasında, uç nokta tanımı belirtir `basicHttpBinding` ve adlı bir bağlama yapılandırması başvurur `Binding1`, aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="5188f-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
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
  </services>   …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5188f-108">Bağlama yapılandırma kümeleri `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) için `Message` ve ayarlar `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)için `Certificate` aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="5188f-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="5188f-109">Hizmetin kendisi için istemci kimlik doğrulaması için kullandığı sertifikayı altında yapılandırma dosyasının davranışları bölümünde ayarlanır `serviceCredentials` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5188f-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="5188f-110">İstemci hizmete kendi kimliğini doğrulamak için kullandığı sertifikayı uygulandığı doğrulama modu da altındaki davranışları bölümünde ayarlandığından `clientCertificate` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5188f-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
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
  
 <span data-ttu-id="5188f-111">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="5188f-112">Arayanın Kimliği hizmet konsol penceresinde aşağıdaki kodu kullanarak görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="5188f-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="5188f-113">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5188f-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5188f-114">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5188f-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="5188f-115">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5188f-115">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="5188f-116">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5188f-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5188f-117">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5188f-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="5188f-118">Aynı makinede örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5188f-118">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="5188f-119">Setup.bat örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="5188f-120">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="5188f-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5188f-121">Setup.bat toplu iş dosyası, Windows SDK komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5188f-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="5188f-122">MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="5188f-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="5188f-123">Bu ortam değişkeni, Windows SDK komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5188f-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2.  <span data-ttu-id="5188f-124">Hizmet uygulaması \service\bin çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-124">Run the service application from \service\bin.</span></span>  
  
3.  <span data-ttu-id="5188f-125">İstemci uygulaması \client\bin çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="5188f-126">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5188f-126">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="5188f-127">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="5188f-127">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
5.  <span data-ttu-id="5188f-128">Sertifikaları örnekle tamamladığınızda Cleanup.bat çalıştırarak kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="5188f-129">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5188f-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="5188f-130">Makine genelinde örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5188f-130">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="5188f-131">Hizmet ikili dosyaları hizmeti makinede bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5188f-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="5188f-132">Hizmet program dosyaları sunucuda hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5188f-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="5188f-133">Ayrıca Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyaları sunucuya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5188f-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3.  <span data-ttu-id="5188f-134">İstemci ikili dosyalarının için istemci makinede bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5188f-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="5188f-135">İstemci makinesinde istemci dizinine istemci program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5188f-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="5188f-136">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5188f-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="5188f-137">Sunucu üzerinde çalışan `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="5188f-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="5188f-138">Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="5188f-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="5188f-139">Yeni sertifika yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) öğesi) makinenin tam etki alanı adı ile aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="5188f-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="5188f-140">Ayrıca localhost yerine bir makine tam adı belirtmek için taban adresi değerini değiştirin`.`</span><span class="sxs-lookup"><span data-stu-id="5188f-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7.  <span data-ttu-id="5188f-141">Service.cer dosya hizmeti dizininden istemci makinesinde istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5188f-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="5188f-142">İstemci üzerinde çalışan `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="5188f-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="5188f-143">Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="5188f-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="5188f-144">İstemci makinesinde Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5188f-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="5188f-145">Bunun için localhost sunucunun tam etki alanı adı ile değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="5188f-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="5188f-146">Aynı zamanda değiştirmeniz `findValue` özniteliği [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) sunucusunun tam etki alanı adı olan yeni hizmet sertifikası adı.</span><span class="sxs-lookup"><span data-stu-id="5188f-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="5188f-147">Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5188f-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="5188f-148">İstemcide ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="5188f-149">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="5188f-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="5188f-150">ImportClientCert.bat, çalıştıran sunucuda, bu istemci sertifikasını Client.cer dosyadan LocalMachine - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="5188f-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="5188f-151">Hizmeti makinede Service.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="5188f-152">İstemci makinesinde, bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="5188f-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1.  <span data-ttu-id="5188f-153">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="5188f-153">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5188f-154">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="5188f-154">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="5188f-155">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5188f-156">Bu komut dosyası, bu örnek makine genelinde çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="5188f-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="5188f-157">Makine genelinde sertifikaları kullanan Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="5188f-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="5188f-158">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="5188f-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5188f-159">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5188f-160">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5188f-160">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5188f-161">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5188f-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5188f-162">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5188f-162">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a><span data-ttu-id="5188f-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5188f-163">See Also</span></span>
