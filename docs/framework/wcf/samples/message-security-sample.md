---
description: 'Daha fazla bilgi edinin: Ileti güvenliği örneği'
title: İleti Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: adec9df3b2a3b5ba022ec2123a8d90d85869246b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752307"
---
# <a name="message-security-sample"></a><span data-ttu-id="cccd7-103">İleti Güvenliği Örneği</span><span class="sxs-lookup"><span data-stu-id="cccd7-103">Message Security Sample</span></span>

<span data-ttu-id="cccd7-104">Bu örnek, ve ileti güvenliğini kullanan bir uygulamanın nasıl uygulanacağını gösterir `basicHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="cccd7-104">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="cccd7-105">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="cccd7-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cccd7-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="cccd7-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cccd7-107">Güvenlik modu `basicHttpBinding` aşağıdaki değerlere ayarlanabilir: `Message` , `Transport` , `TransportWithMessageCredential` , `TransportCredentialOnly` ve `None` .</span><span class="sxs-lookup"><span data-stu-id="cccd7-107">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="cccd7-108">Aşağıdaki örnek Service App.config dosyasında, uç nokta tanımı ' `basicHttpBinding` ı belirtir ve `Binding1` Aşağıdaki örnek yapılandırmada gösterildiği gibi, adlı bir bağlama yapılandırmasına başvurur:</span><span class="sxs-lookup"><span data-stu-id="cccd7-108">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="cccd7-109">Bağlama yapılandırması `mode` , öğesinin özniteliğini [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) olarak ayarlar `Message` ve `clientCredentialType` öğesinin özniteliğini [\<message>](../../configure-apps/file-schema/wcf/message-of-basichttpbinding.md) `Certificate` Aşağıdaki örnek yapılandırmada gösterildiği gibi olarak ayarlar:</span><span class="sxs-lookup"><span data-stu-id="cccd7-109">The binding configuration sets the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="cccd7-110">Hizmetin istemcinin kimliğini doğrulamak için kullandığı sertifika, öğesinin altındaki yapılandırma dosyasının davranışlar bölümünde ayarlanır `serviceCredentials` .</span><span class="sxs-lookup"><span data-stu-id="cccd7-110">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="cccd7-111">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifika için geçerli olan doğrulama modu, öğesinin altındaki davranışlar bölümünde de ayarlanır `clientCertificate` .</span><span class="sxs-lookup"><span data-stu-id="cccd7-111">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
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
  
 <span data-ttu-id="cccd7-112">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cccd7-112">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="cccd7-113">Arayanın kimliği, aşağıdaki kod kullanılarak hizmet konsolu penceresinde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="cccd7-113">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="cccd7-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cccd7-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="cccd7-115">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-115">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="cccd7-116">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="cccd7-116">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="cccd7-117">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cccd7-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cccd7-118">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cccd7-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="cccd7-119">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cccd7-119">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="cccd7-120">Örnek yüklemesi klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-120">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="cccd7-121">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="cccd7-121">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cccd7-122">Setup.bat Batch dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cccd7-122">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="cccd7-123">MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cccd7-123">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="cccd7-124">Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cccd7-124">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2. <span data-ttu-id="cccd7-125">Hizmet uygulamasını \service\bin. adresinden çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cccd7-125">Run the service application from \service\bin.</span></span>  
  
3. <span data-ttu-id="cccd7-126">\Client\bin. adresinden istemci uygulamasını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cccd7-126">Run the client application from \client\bin.</span></span> <span data-ttu-id="cccd7-127">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cccd7-127">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="cccd7-128">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="cccd7-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5. <span data-ttu-id="cccd7-129">Örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-129">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="cccd7-130">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="cccd7-130">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="cccd7-131">Örneği makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cccd7-131">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="cccd7-132">Hizmet ikili dosyaları için hizmet makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cccd7-132">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="cccd7-133">Hizmet programı dosyalarını sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-133">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="cccd7-134">Ayrıca Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını sunucuya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-134">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3. <span data-ttu-id="cccd7-135">İstemci ikili dosyaları için istemci makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cccd7-135">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="cccd7-136">İstemci programı dosyalarını istemci makinesindeki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-136">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="cccd7-137">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-137">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="cccd7-138">Sunucusunda öğesini çalıştırın `setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="cccd7-138">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="cccd7-139">`setup.bat` `service` Bağımsız değişkeniyle birlikte çalıştırmak makinenin tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="cccd7-139">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="cccd7-140">Service.exe.config, `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) makinenin tam etki alanı adıyla aynı olan yeni sertifika adını (öğesindeki özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="cccd7-140">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="cccd7-141">Ayrıca, temel adresin değerini localhost yerine tam bir makine adı belirtecek şekilde değiştirin`.`</span><span class="sxs-lookup"><span data-stu-id="cccd7-141">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7. <span data-ttu-id="cccd7-142">Service. cer dosyasını hizmet dizininden istemci makinesindeki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-142">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="cccd7-143">İstemcisinde öğesini çalıştırın `setup.bat client` .</span><span class="sxs-lookup"><span data-stu-id="cccd7-143">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="cccd7-144">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `client` Client.com adlı bir istemci sertifikası oluşturur ve Istemci sertifikasını Client. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="cccd7-144">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="cccd7-145">İstemci makinesindeki Client.exe.config dosyasında, bitiş noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cccd7-145">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="cccd7-146">Bunu, localhost yerine sunucunun tam etki alanı adıyla değiştirerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cccd7-146">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="cccd7-147">Ayrıca `findValue` , öğesinin özniteliğini [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) sunucusunun tam etki alanı adı olan yeni hizmet sertifikası adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cccd7-147">Also change the `findValue` attribute of the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="cccd7-148">Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-148">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="cccd7-149">İstemcisinde ImportServiceCert.bat ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-149">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="cccd7-150">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="cccd7-150">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="cccd7-151">Sunucusunda ImportClientCert.bat çalıştırın, bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="cccd7-151">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="cccd7-152">Hizmet makinesinde, bir komut isteminden Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-152">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="cccd7-153">İstemci makinesinde, bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-153">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1. <span data-ttu-id="cccd7-154">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="cccd7-154">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="cccd7-155">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="cccd7-155">To clean up after the sample</span></span>  
  
- <span data-ttu-id="cccd7-156">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cccd7-156">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cccd7-157">Bu betik, makineler arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="cccd7-157">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="cccd7-158">Makinelerde sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cccd7-158">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="cccd7-159">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="cccd7-159">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cccd7-160">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cccd7-160">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cccd7-161">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cccd7-161">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cccd7-162">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cccd7-162">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cccd7-163">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cccd7-163">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`
