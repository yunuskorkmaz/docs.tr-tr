---
title: İleti Güvenliği Kullanıcı Adı
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
author: BrucePerlerMS
ms.openlocfilehash: 904916424c3ab199afd09a804c47b57a82e14158
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030807"
---
# <a name="message-security-user-name"></a><span data-ttu-id="491a2-102">İleti Güvenliği Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="491a2-102">Message Security User Name</span></span>
<span data-ttu-id="491a2-103">Bu örnek, kullanıcı adı kimlik doğrulaması için istemci ile WS-güvenlik kullanan ve sunucusunun X.509v3 sertifikasını kullanarak kimlik doğrulaması gerektiren bir uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="491a2-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="491a2-104">Tüm uygulama iletileri istemci ve sunucu arasında imzalanmış ve şifrelenmiş.</span><span class="sxs-lookup"><span data-stu-id="491a2-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="491a2-105">Varsayılan olarak, kullanıcı adı ve parolanızı, istemci tarafından kullanılan oturum açmak için geçerli bir Windows hesabı.</span><span class="sxs-lookup"><span data-stu-id="491a2-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="491a2-106">Bu örnek dayanır [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="491a2-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="491a2-107">Bu örnek, bir istemci konsol programı'nı (Client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (Service.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="491a2-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="491a2-108">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="491a2-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="491a2-109">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="491a2-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="491a2-110">Bu örnek ayrıca gösterir:</span><span class="sxs-lookup"><span data-stu-id="491a2-110">This sample also demonstrates:</span></span>  
  
-   <span data-ttu-id="491a2-111">Ek yetkilendirme gerçekleştirilebilir için varsayılan Windows hesaplarına eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="491a2-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
-   <span data-ttu-id="491a2-112">Arayanın kimlik bilgileri hizmet kodundan erişim yapma.</span><span class="sxs-lookup"><span data-stu-id="491a2-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="491a2-113">Hizmet, Web.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="491a2-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="491a2-114">Bir standart yapılandırılmış bağlama [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), bunun varsayılan ileti güveliği kullanarak için.</span><span class="sxs-lookup"><span data-stu-id="491a2-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="491a2-115">Bu örnek, standart ayarlar [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) istemci kullanıcı adı kimlik doğrulaması kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="491a2-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="491a2-116">Davranış hizmeti kimlik doğrulaması için kullanılacak olan kullanıcı kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="491a2-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="491a2-117">Sunucu sertifikasının konu adı olarak aynı değeri içermelidir `findValue` özniteliğini [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="491a2-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="491a2-118">İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin oluşur.</span><span class="sxs-lookup"><span data-stu-id="491a2-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="491a2-119">Bağlama istemcinin uygun olarak yapılandırıldığı `securityMode` ve `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="491a2-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="491a2-120">Bilgisayarlar arası senaryoda çalıştırırken, hizmet uç noktası adresi uygun şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="491a2-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="491a2-121">İstemci uygulaması, kullanıcı adını ve parolayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="491a2-121">The client implementation sets the user name and password to use.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 <span data-ttu-id="491a2-122">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="491a2-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="491a2-123">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="491a2-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="491a2-124">MessageSecurity örnekleriyle dahil Setup.bat toplu iş dosyası sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili bir sertifika sunucusu yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="491a2-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="491a2-125">Toplu iş dosyasını iki modda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="491a2-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="491a2-126">Tek bilgisayarlı modunda toplu iş dosyasını çalıştırmak için şunu yazın `setup.bat` komut satırına.</span><span class="sxs-lookup"><span data-stu-id="491a2-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="491a2-127">Hizmet modu türü içinde çalıştırmak için `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="491a2-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="491a2-128">Örnek bilgisayarlar arasında çalıştırırken bu modu kullanın.</span><span class="sxs-lookup"><span data-stu-id="491a2-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="491a2-129">Ayrıntılar için bu konunun sonunda Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="491a2-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="491a2-130">Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="491a2-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="491a2-131">Sunucu sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="491a2-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="491a2-132">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="491a2-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="491a2-133">% Sunucu_adı % değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="491a2-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="491a2-134">Depolanmış bir sertifikayla LocalMachine depolama.</span><span class="sxs-lookup"><span data-stu-id="491a2-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="491a2-135">Setup.bat toplu iş dosyasını hizmet bağımsız değişkenlerle çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="491a2-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="491a2-136">Aksi takdirde localhost için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="491a2-136">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="491a2-137">İstemcinin güvenilen sertifika deposuna sunucu sertifikası yükleme</span><span class="sxs-lookup"><span data-stu-id="491a2-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="491a2-138">Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="491a2-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="491a2-139">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="491a2-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="491a2-140">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="491a2-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="491a2-141">Sertifikanın özel anahtarı izin verme</span><span class="sxs-lookup"><span data-stu-id="491a2-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="491a2-142">Sunucu sertifikası için erişilebilir LocalMachine deposunda depolanır Setup.bat toplu iş dosyasında aşağıdaki satırları olun [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] çalışan işlem hesabı.</span><span class="sxs-lookup"><span data-stu-id="491a2-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="491a2-143">ABD dışı kullanıyorsanız Setup.bat dosyasını düzenleyin ve yerini Windows İngilizce sürümünü `NT AUTHORITY\NETWORK SERVICE` , bölgesel karşılığı hesap adıyla.</span><span class="sxs-lookup"><span data-stu-id="491a2-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="491a2-144">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="491a2-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="491a2-145">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="491a2-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="491a2-146">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="491a2-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="491a2-147">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="491a2-147">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="491a2-148">Yolun Makecert.exe ve FindPrivateKey.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="491a2-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="491a2-149">Yönetici ayrıcalıklarıyla açılan bir Visual Studio komut istemi örnek yükleme klasöründe Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="491a2-149">Run Setup.bat from the sample install folder in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="491a2-150">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="491a2-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="491a2-151">Setup.bat toplu iş dosyası, bir Visual Studio komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="491a2-151">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt.</span></span> <span data-ttu-id="491a2-152">Bu, path ortam değişkenine'nın SDK'ın yüklendiği dizini gösterecek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="491a2-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="491a2-153">Bu ortam değişkeni, bir Visual Studio komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="491a2-153">This environment variable is automatically set within a Visual Studio Command Prompt.</span></span>  
  
3.  <span data-ttu-id="491a2-154">Adresini girerek bir tarayıcı kullanarak hizmetine erişiminizi doğrulayın http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="491a2-154">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="491a2-155">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="491a2-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="491a2-156">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="491a2-156">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="491a2-157">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="491a2-157">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="491a2-158">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="491a2-158">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="491a2-159">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="491a2-159">Create a directory on the service computer.</span></span> <span data-ttu-id="491a2-160">Internet Information Services yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="491a2-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2.  <span data-ttu-id="491a2-161">Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="491a2-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="491a2-162">Dosyaları \bin alt dizinde kopyalama emin olun.</span><span class="sxs-lookup"><span data-stu-id="491a2-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="491a2-163">Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="491a2-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="491a2-164">İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="491a2-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="491a2-165">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="491a2-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="491a2-166">Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="491a2-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="491a2-167">Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="491a2-167">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="491a2-168">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="491a2-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="491a2-169">Bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adı (serviceCertificate öğesindeki findValue özniteliği) yansıtacak şekilde Web.config Düzenle`.`</span><span class="sxs-lookup"><span data-stu-id="491a2-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7.  <span data-ttu-id="491a2-170">Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="491a2-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="491a2-171">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="491a2-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="491a2-172">İstemcide ImportServiceCert.bat yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="491a2-172">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="491a2-173">Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="491a2-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="491a2-174">İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="491a2-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="491a2-175">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="491a2-175">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="491a2-176">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="491a2-176">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="491a2-177">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="491a2-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="491a2-178">Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="491a2-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="491a2-179">Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun.</span><span class="sxs-lookup"><span data-stu-id="491a2-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="491a2-180">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="491a2-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491a2-181">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="491a2-181">See Also</span></span>
