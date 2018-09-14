---
title: Özel Bağlama Güvenliği
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 61e8be6f7f621340a684bff69ec5c9d64ab36c61
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45568481"
---
# <a name="custom-binding-security"></a><span data-ttu-id="14956-102">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="14956-102">Custom Binding Security</span></span>
<span data-ttu-id="14956-103">Bu örnek, özel bir bağlama kullanarak güvenlik yapılandırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="14956-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="14956-104">Bu, özel bağlama güvenli aktarım birlikte ileti düzeyi güvenliği etkinleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="14956-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="14956-105">Bu hizmet ve istemci arasında ileti aktarmaya güvenli aktarım gereklidir ve iletileri ileti düzeyi üzerinde aynı anda güvenli olmalıdır yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="14956-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="14956-106">Bu yapılandırma, sistem tarafından sağlanan bağlamalar tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="14956-106">This configuration is not supported by system-provided bindings.</span></span>  
  
 <span data-ttu-id="14956-107">Bu örnek, bir istemci konsol programı'nı (EXE) ve hizmeti bir konsol programı (EXE) oluşur.</span><span class="sxs-lookup"><span data-stu-id="14956-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="14956-108">Hizmet, çift yönlü sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="14956-108">The service implements a duplex contract.</span></span> <span data-ttu-id="14956-109">Anlaşma tarafından tanımlanan `ICalculatorDuplex` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="14956-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="14956-110">`ICalculatorDuplex` Oturumu üzerinden çalışan bir sonuç hesaplama matematik işlemlerini gerçekleştirmek üzere istemci arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="14956-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="14956-111">Hizmet üzerinde bağımsız olarak, sonuçlar döndürebilir `ICalculatorDuplexCallback` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="14956-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="14956-112">Hizmet ve istemci arasında gönderilen ileti kümesini ilişkilendirmek için bir bağlamı yeniden kurulması için çift yönlü sözleşme bir oturumu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="14956-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="14956-113">Özel bağlama güvenli ve çift yönlü iletişimi destekleyen tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="14956-113">A custom binding is defined that supports duplex communication and is secure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14956-114">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="14956-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="14956-115">Hizmet yapılandırması aşağıdaki destekleyen özel bir bağlama tanımlar:</span><span class="sxs-lookup"><span data-stu-id="14956-115">The service configuration defines a custom binding that supports the following:</span></span>  
  
-   <span data-ttu-id="14956-116">TLS/SSL protokolü kullanılarak korunan TCP iletişimi.</span><span class="sxs-lookup"><span data-stu-id="14956-116">TCP communication protected by using the TLS/SSL protocol.</span></span>  
  
-   <span data-ttu-id="14956-117">İleti güvenliği Windows.</span><span class="sxs-lookup"><span data-stu-id="14956-117">Windows message security.</span></span>  
  
 <span data-ttu-id="14956-118">Özel bağlama yapılandırması güvenli aktarım ileti düzeyi güvenliği aynı anda etkinleştirerek sağlar.</span><span class="sxs-lookup"><span data-stu-id="14956-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="14956-119">Bağlama öğelerinin sıralama her bir katman kanal yığınında temsil ettiği için bir özel bağlamayı tanımlamak önemlidir (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="14956-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="14956-120">Özel bağlama hizmeti ve istemci yapılandırma dosyalarını, aşağıdaki örnek yapılandırmada gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="14956-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="14956-121">Özel bağlama taşıma düzeyinde hizmet kimliğini doğrulamak ve istemci ile hizmet arasında iletim sırasında mesajlarını korumak için bir hizmet sertifikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="14956-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="14956-122">Bu tarafından gerçekleştirilir `sslStreamSecurity` bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="14956-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="14956-123">Hizmet sertifikası, aşağıdaki örnek yapılandırmada gösterildiği gibi bir hizmet davranışını kullanarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="14956-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata />  
        <serviceDebug includeExceptionDetailInFaults="False" />  
        <serviceCredentials>  
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
        </serviceCredentials>  
    </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="14956-124">Ayrıca, özel bağlamanın Windows kimlik bilgisi türü ile ileti güvenliği kullanır - bu varsayılan kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="14956-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="14956-125">Bu tarafından gerçekleştirilir `security` bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="14956-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="14956-126">Hizmet ve istemci, Kerberos kimlik doğrulama mekanizması varsa, ileti düzeyi güvenliği kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="14956-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="14956-127">Bu örnek Active Directory ortamında çalışırsa gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="14956-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="14956-128">Kerberos kimlik doğrulama mekanizması kullanılabilir durumda değilse, NTLM kimlik doğrulaması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14956-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="14956-129">NTLM bir hizmete istemcinin kimliğini doğrular, ancak istemci hizmete kimlik doğrulaması yapmaz.</span><span class="sxs-lookup"><span data-stu-id="14956-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="14956-130">`security` Bağlama öğesi kullanacak şekilde yapılandırıldığını `SecureConversation``authenticationType`, hem istemci hem de hizmet üzerinde bir güvenlik oturumu oluşturulmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="14956-130">The `security` binding element is configured to use `SecureConversation``authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="14956-131">Bu, hizmetin çalışması çift yönlü sözleşme etkinleştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="14956-131">This is required to enable the service's duplex contract to work.</span></span>  
  
 <span data-ttu-id="14956-132">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemcinin konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="14956-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="14956-133">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="14956-133">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="14956-134">Örneği çalıştırdığında üzerinde istemciye döndürülen iletileri bkz hizmetinden gönderilen geri çağırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="14956-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="14956-135">Tüm işlemler tamamlandıktan sonra tüm denklemi ardından her ara sonuçlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="14956-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="14956-136">İstemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="14956-136">Press ENTER to shut down the client.</span></span>  
  
 <span data-ttu-id="14956-137">Dahil edilen Setup.bat dosyasının, istemci ve sunucu sertifikası tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili hizmet sertifikası ile yapılandırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="14956-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="14956-138">Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="14956-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="14956-139">Bu örnek için geçerlidir ve böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="14956-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="14956-140">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="14956-140">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="14956-141">Setup.bat dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14956-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="14956-142">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="14956-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="14956-143">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14956-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="14956-144">Bu toplu dosya sunucusu adı için localhost varsayar.</span><span class="sxs-lookup"><span data-stu-id="14956-144">This batch file defaults the server name to localhost.</span></span>  
  
     <span data-ttu-id="14956-145">Depolanmış bir sertifikayla Web barındırılan hizmetleri CurrentUser deposunda.</span><span class="sxs-lookup"><span data-stu-id="14956-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="14956-146">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="14956-146">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="14956-147">İstemci güvenilir kişiler uygulamasına Setup.bat dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="14956-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="14956-148">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="14956-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="14956-149">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="14956-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="14956-150">Setup.bat toplu iş dosyası, bir Visual Studio 2010 komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="14956-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="14956-151">MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="14956-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="14956-152">Bu ortam değişkeni, bir Visual Studio 2010 Komut İstemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="14956-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="14956-153">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="14956-153">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="14956-154">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14956-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="14956-155">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14956-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="14956-156">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14956-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="14956-157">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="14956-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="14956-158">Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi penceresi açın ve örnek yükleme klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="14956-158">Open a Visual Studio Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="14956-159">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="14956-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="14956-160">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="14956-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="14956-161">İçinde PATH ortam değişkenini ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="14956-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="14956-162">Service.exe \service\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="14956-162">Launch Service.exe from \service\bin.</span></span>  
  
3.  <span data-ttu-id="14956-163">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="14956-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="14956-164">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="14956-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="14956-165">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="14956-165">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="14956-166">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="14956-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="14956-167">Hizmet bilgisayarda:</span><span class="sxs-lookup"><span data-stu-id="14956-167">On the service computer:</span></span>  
  
    1.  <span data-ttu-id="14956-168">Hizmeti bilgisayarında servicemodelsamples adlı sanal bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14956-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2.  <span data-ttu-id="14956-169">Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="14956-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="14956-170">Dosyaları \bin alt dizinde kopyalama emin olun.</span><span class="sxs-lookup"><span data-stu-id="14956-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3.  <span data-ttu-id="14956-171">Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="14956-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4.  <span data-ttu-id="14956-172">Yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde aşağıdaki komutu çalıştırın: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="14956-172">Run the following command in a Visual Studio command prompt opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="14956-173">Bu, toplu iş dosyasını çalıştırmak bilgisayarın adı ile eşleşen bir konu adına sahip hizmet sertifikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14956-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="14956-174">Setup.bat toplu iş dosyası, bir Visual Studio 2010 komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="14956-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="14956-175">Bu, path ortam değişkenine'nın SDK'ın yüklendiği dizini gösterecek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="14956-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="14956-176">Bu ortam değişkeni, bir Visual Studio 2010 Komut İstemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="14956-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
    5.  <span data-ttu-id="14956-177">Değişiklik [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) önceki adımda oluşturulan sertifikanın konu adı yansıtacak şekilde Service.exe.config dosyasının içinde.</span><span class="sxs-lookup"><span data-stu-id="14956-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>  
  
    6.  <span data-ttu-id="14956-178">Service.exe, bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="14956-178">Run Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="14956-179">İstemci bilgisayarda:</span><span class="sxs-lookup"><span data-stu-id="14956-179">On the client computer:</span></span>  
  
    1.  <span data-ttu-id="14956-180">İstemci program dosyaları \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="14956-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="14956-181">Ayrıca Cleanup.bat dosyasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="14956-181">Also copy the Cleanup.bat file.</span></span>  
  
    2.  <span data-ttu-id="14956-182">Önceki örneklerinden herhangi bir eski sertifika kaldırmak için Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="14956-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>  
  
    3.  <span data-ttu-id="14956-183">Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açıp hizmet bilgisayarda aşağıdaki komutu çalıştırarak hizmetin sertifikayı dışarı aktarma (yerine `%SERVER_NAME%` hizmeti, bilgisayarın tam olarak nitelenmiş ada sahip çalışan):</span><span class="sxs-lookup"><span data-stu-id="14956-183">Export the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  <span data-ttu-id="14956-184">%SERVER_NAME%.cer (yerine % sunucu_adı % tam olarak nitelenmiş adda hizmetinin çalıştığı bilgisayarın) istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="14956-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>  
  
    5.  <span data-ttu-id="14956-185">Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açıp aşağıdaki komutu (yedek sunucu_adı % tam olarak nitelenmiş adda hizmeti, bilgisayarın istemci bilgisayarda çalışan hizmetin sertifika alma çalışan):</span><span class="sxs-lookup"><span data-stu-id="14956-185">Import the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         <span data-ttu-id="14956-186">Adımları c, d ve e güvenilen veren tarafından sertifika verilirse gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="14956-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>  
  
    6.  <span data-ttu-id="14956-187">İstemcinin App.config dosyasını aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="14956-187">Modify the client’s App.config file as follows:</span></span>  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  <span data-ttu-id="14956-188">Hizmet bir dışında NetworkService hesabı veya etki alanı ortamında LocalSystem hesabı altında çalışıyorsa, istemcinin App.config dosyasında uygun UPN veya SPN tabanlı ayarlamak için hizmet uç noktası için uç nokta kimliğini değiştirmeniz gerekebilir hesapta, hizmeti çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14956-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="14956-189">Uç nokta kimlik hakkında daha fazla bilgi için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) konu.</span><span class="sxs-lookup"><span data-stu-id="14956-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>  
  
    8.  <span data-ttu-id="14956-190">Client.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="14956-190">Run Client.exe from a command prompt.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="14956-191">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="14956-191">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="14956-192">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="14956-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14956-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14956-193">See Also</span></span>
