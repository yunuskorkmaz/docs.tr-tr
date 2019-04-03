---
title: İleti Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 23304ba3be88e327f84943daf0dcd751d564d5f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825592"
---
# <a name="message-security-sample"></a><span data-ttu-id="c8043-102">İleti Güvenliği Örneği</span><span class="sxs-lookup"><span data-stu-id="c8043-102">Message Security Sample</span></span>
<span data-ttu-id="c8043-103">Bu örnek kullanan bir uygulamanın nasıl uygulanacağını gösterir `basicHttpBinding` güvenlik iletisi.</span><span class="sxs-lookup"><span data-stu-id="c8043-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="c8043-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.</span><span class="sxs-lookup"><span data-stu-id="c8043-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8043-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c8043-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c8043-106">Güvenlik modu `basicHttpBinding` aşağıdaki değerleri ayarlayın: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="c8043-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="c8043-107">Aşağıdaki örnek hizmet App.config dosyasında, uç nokta tanımı belirtir `basicHttpBinding` ve adlı bir bağlama yapılandırmasını başvurur `Binding1`aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="c8043-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="c8043-108">Bağlama yapılandırma kümeleri `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) için `Message` ve ayarlar `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)için `Certificate` aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="c8043-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="c8043-109">Hizmetin kendisini istemcinin kimliğini doğrulamak için kullandığı sertifikayı davranışları bölümü altında yapılandırma dosyasının kümesindeki `serviceCredentials` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c8043-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="c8043-110">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifikayı uygulandığı doğrulama modu da davranışları bölümünde ayarlanır `clientCertificate` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c8043-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
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
  
 <span data-ttu-id="c8043-111">Aynı bağlama ve güvenlik ayrıntıları, istemci yapılandırma dosyasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c8043-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="c8043-112">Çağıranın kimliğini, hizmet konsol penceresinde aşağıdaki kodu kullanarak görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="c8043-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="c8043-113">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c8043-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c8043-114">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c8043-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="c8043-115">Ayarlama ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c8043-115">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="c8043-116">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8043-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c8043-117">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8043-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="c8043-118">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c8043-118">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="c8043-119">Setup.bat örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8043-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="c8043-120">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="c8043-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c8043-121">Setup.bat toplu iş dosyası, bir Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8043-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="c8043-122">MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="c8043-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="c8043-123">Bu ortam değişkeni, bir Windows SDK komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c8043-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2.  <span data-ttu-id="c8043-124">Hizmet uygulaması \service\bin çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8043-124">Run the service application from \service\bin.</span></span>  
  
3.  <span data-ttu-id="c8043-125">\Client\bin istemci uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8043-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="c8043-126">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c8043-126">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="c8043-127">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c8043-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5.  <span data-ttu-id="c8043-128">Örnek ile tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c8043-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="c8043-129">Diğer güvenlik örnekleri aynı sertifikalarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8043-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="c8043-130">Makineler arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c8043-130">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="c8043-131">Hizmet makinede hizmet ikili dosyaları için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8043-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="c8043-132">Hizmet program dosyaları sunucuda hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c8043-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="c8043-133">Ayrıca Setup.bat Cleanup.bat ve ImportClientCert.bat dosyaları sunucuya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c8043-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3.  <span data-ttu-id="c8043-134">İstemci ikili dosyaları için istemci makinede bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8043-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="c8043-135">İstemci makinesinde istemci dizinine istemci program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c8043-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="c8043-136">Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c8043-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="c8043-137">Sunucu üzerinde çalışan `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="c8043-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="c8043-138">Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="c8043-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="c8043-139">Yeni sertifika adını yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) öğesi) makinesinin tam etki alanı adıyla aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="c8043-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="c8043-140">Ayrıca temel adresini localhost yerine tam makine adını değiştirin`.`</span><span class="sxs-lookup"><span data-stu-id="c8043-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7.  <span data-ttu-id="c8043-141">Service.cer dosya hizmeti dizininden istemci makine üzerinde istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c8043-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="c8043-142">Bir istemcide çalışmasına `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="c8043-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="c8043-143">Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="c8043-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="c8043-144">İstemci makinesinde Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c8043-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="c8043-145">Localhost sunucunun tam etki alanı adıyla değiştirerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8043-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="c8043-146">Ayrıca `findValue` özniteliği [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) sunucusunun tam etki alanı adı olan yeni hizmet sertifikası adı.</span><span class="sxs-lookup"><span data-stu-id="c8043-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="c8043-147">Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c8043-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="c8043-148">İstemcide ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8043-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="c8043-149">Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="c8043-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="c8043-150">ImportClientCert.bat, çalıştıran sunucuda bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposu içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="c8043-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="c8043-151">Hizmeti makinede Service.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8043-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="c8043-152">İstemci makinesinde bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="c8043-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1.  <span data-ttu-id="c8043-153">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c8043-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c8043-154">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="c8043-154">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="c8043-155">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8043-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c8043-156">Bu betik, bu örnek makinelerde çalışan hizmet sertifikaları bir istemci üzerinde kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="c8043-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="c8043-157">Makinelerde sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun.</span><span class="sxs-lookup"><span data-stu-id="c8043-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c8043-158">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="c8043-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8043-159">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="c8043-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8043-160">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c8043-160">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c8043-161">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c8043-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8043-162">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c8043-162">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
