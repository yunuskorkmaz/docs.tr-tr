---
title: "İleti Güvenliği Kullanıcı Adı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
caps.latest.revision: "57"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3d0c5278cf1860a89ea6a1c3ed33b45ed3c48e92
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-user-name"></a><span data-ttu-id="0a0a9-102">İleti Güvenliği Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="0a0a9-102">Message Security User Name</span></span>
<span data-ttu-id="0a0a9-103">Bu örnek, istemci için kullanıcı adı kimlik doğrulaması ile WS güvenliği kullanan ve sunucunun X.509v3 sertifikasını kullanarak kimlik doğrulaması gerektiren bir uygulama uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="0a0a9-104">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="0a0a9-105">Varsayılan olarak, kullanıcı adı ve istemci tarafından sağlanan parola kullanılan oturum açmak için geçerli bir Windows hesabı.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="0a0a9-106">Bu örnek dayanır [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0a0a9-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="0a0a9-107">Bu örnek, bir istemci konsol programı (Client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (Service.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="0a0a9-108">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a0a9-109">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0a0a9-110">Bu örnek ayrıca gösterir:</span><span class="sxs-lookup"><span data-stu-id="0a0a9-110">This sample also demonstrates:</span></span>  
  
-   <span data-ttu-id="0a0a9-111">Böylece ek yetkilendirme gerçekleştirilebilir varsayılan Windows hesaplarına eşleme.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
-   <span data-ttu-id="0a0a9-112">Hizmet kodundan Arayanın kimlik bilgilerine erişmek nasıl.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="0a0a9-113">Hizmet Web.config yapılandırma dosyası kullanarak tanımlanan hizmeti ile iletişim için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="0a0a9-114">Bağlama ile standart bir yapılandırılmış [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ileti güvenliği için kullanılacak varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="0a0a9-115">Bu örnek standart ayarlar [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) istemci kullanıcı adı kimlik doğrulaması kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="0a0a9-116">Kullanıcı kimlik bilgilerini hizmet kimlik doğrulaması için kullanılacak olan davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="0a0a9-117">Sunucu sertifikasının konu adı olarak aynı değeri içermelidir `findValue` özniteliğini [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="0a0a9-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="0a0a9-118">Hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="0a0a9-119">Bağlama istemci uygun ile yapılandırılmış `securityMode` ve `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="0a0a9-120">Bilgisayarlar arası senaryoda çalıştırırken, hizmet uç noktası adresi uygun şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="0a0a9-121">İstemci uygulama kullanıcı adı ve parola ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-121">The client implementation sets the user name and password to use.</span></span>  
  
```  
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
  
 <span data-ttu-id="0a0a9-122">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0a0a9-123">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="0a0a9-124">MessageSecurity örnekleriyle dahil Setup.bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için uygun bir sertifikayı sunucu yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="0a0a9-125">Toplu iş dosyası iki modda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="0a0a9-126">Tek bilgisayar modunda toplu iş dosyasını çalıştırmak için şunu yazın `setup.bat` komut satırında.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="0a0a9-127">Hizmet modu türü çalıştırmak için `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="0a0a9-128">Örnek bilgisayarlar arasında çalıştırırken bu modunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="0a0a9-129">Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="0a0a9-130">Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="0a0a9-131">Sunucu sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a0a9-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="0a0a9-132">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="0a0a9-133">% Sunucu_adı % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="0a0a9-134">Sertifika saklanır LocalMachine deposundaki.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="0a0a9-135">Bir hizmet bağımsız değişkeniyle Setup.bat toplu iş dosyası çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="0a0a9-136">Aksi takdirde localhost için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-136">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="0a0a9-137">İstemcinin güvenilen sertifika deposuna sunucu sertifikası yükleme</span><span class="sxs-lookup"><span data-stu-id="0a0a9-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="0a0a9-138">Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="0a0a9-139">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="0a0a9-140">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="0a0a9-141">Sertifikanın özel anahtarı izin verme</span><span class="sxs-lookup"><span data-stu-id="0a0a9-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="0a0a9-142">Erişilebilir LocalMachine deposundaki depolanan sunucu sertifikası Setup.bat toplu iş dosyası aşağıdaki satırları olun [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] çalışan işlem hesabı.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```  
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
    >  <span data-ttu-id="0a0a9-143">ABD dışındaki kullanıyorsanız Setup.bat dosyasını düzenleyin ve yerini Windows İngilizce sürümünü `NT AUTHORITY\NETWORK SERVICE` bölgesel eşdeğer. hesap adı.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0a0a9-144">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="0a0a9-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0a0a9-145">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a0a9-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0a0a9-146">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a0a9-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="0a0a9-147">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0a0a9-147">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="0a0a9-148">Yolun Makecert.exe ve FindPrivateKey.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="0a0a9-149">Visual Studio komut istemini yönetici ayrıcalıklarıyla açılmış örnek yükleme klasöründeki Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-149">Run Setup.bat from the sample install folder in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="0a0a9-150">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a0a9-151">Setup.bat toplu iş dosyası, Visual Studio komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-151">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt.</span></span> <span data-ttu-id="0a0a9-152">Path ortam değişkeni SDK yüklendiği dizinine işaret etmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="0a0a9-153">Bu ortam değişkenine bir Visual Studio komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-153">This environment variable is automatically set within a Visual Studio Command Prompt.</span></span>  
  
3.  <span data-ttu-id="0a0a9-154">Adres http://localhost/servicemodelsamples/service.svc girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-154">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="0a0a9-155">Launch Client.exe from \client\bin.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="0a0a9-156">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-156">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="0a0a9-157">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="0a0a9-157">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="0a0a9-158">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0a0a9-158">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="0a0a9-159">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-159">Create a directory on the service computer.</span></span> <span data-ttu-id="0a0a9-160">Internet Information Services yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2.  <span data-ttu-id="0a0a9-161">Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="0a0a9-162">\Bin alt dizinindeki dosyaları kopyalayın emin olun.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="0a0a9-163">Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="0a0a9-164">İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="0a0a9-165">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="0a0a9-166">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="0a0a9-167">Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-167">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="0a0a9-168">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="0a0a9-169">Web.config dosyasını bilgisayarın tam etki alanı adı ile aynı olan yeni sertifika adını (findValue özniteliği serviceCertificate öğesindeki) yansıtacak şekilde düzenleyin`.`</span><span class="sxs-lookup"><span data-stu-id="0a0a9-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7.  <span data-ttu-id="0a0a9-170">Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="0a0a9-171">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="0a0a9-172">İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-172">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="0a0a9-173">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="0a0a9-174">İstemci bilgisayarda bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="0a0a9-175">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="0a0a9-175">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0a0a9-176">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="0a0a9-176">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="0a0a9-177">Örnek çalıştıran bitirdikten sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a0a9-178">Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="0a0a9-179">Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-179">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="0a0a9-180">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0a9-181">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a0a9-181">See Also</span></span>
