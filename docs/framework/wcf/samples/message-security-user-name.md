---
title: İleti Güvenliği Kullanıcı Adı
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183505"
---
# <a name="message-security-user-name"></a><span data-ttu-id="fa8be-102">İleti Güvenliği Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="fa8be-102">Message Security User Name</span></span>
<span data-ttu-id="fa8be-103">Bu örnek, istemci için kullanıcı adı kimlik doğrulaması ile WS-Security kullanan bir uygulamanın nasıl uygulanacağını ve sunucunun X.509v3 sertifikasını kullanarak sunucu kimlik doğrulamasını nasıl gerektirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="fa8be-104">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="fa8be-105">Varsayılan olarak, istemci tarafından sağlanan kullanıcı adı ve parola geçerli bir Windows hesabına oturum açmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa8be-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="fa8be-106">Bu örnek [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa8be-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="fa8be-107">Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programı (Client.exe) ve bir hizmet kitaplığından (Service.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="fa8be-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="fa8be-108">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="fa8be-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa8be-109">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="fa8be-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fa8be-110">Bu örnek aynı zamanda şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="fa8be-110">This sample also demonstrates:</span></span>  
  
- <span data-ttu-id="fa8be-111">Ek yetkilendirme yapIlebilmek için Windows hesaplarına varsayılan eşleme.</span><span class="sxs-lookup"><span data-stu-id="fa8be-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
- <span data-ttu-id="fa8be-112">Arayan kişinin kimlik bilgilerine hizmet kodundan nasıl erişilir?</span><span class="sxs-lookup"><span data-stu-id="fa8be-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="fa8be-113">Hizmet, Web.config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir bitiş noktasını ortaya çıkarır. Bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="fa8be-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="fa8be-114">Bağlama, ileti güvenliğini kullanmak varsayılan standart [ \<bir wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="fa8be-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="fa8be-115">Bu örnek, istemci kullanıcı adı kimlik doğrulaması kullanmak için standart [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fa8be-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="fa8be-116">Davranış, kullanıcı kimlik bilgilerinin hizmet kimlik doğrulaması için kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="fa8be-117">Sunucu sertifikası, [ \<hizmetKimlik Bilgileri>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)özniteliği `findValue` yle özne adı için aynı değeri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="fa8be-118">İstemci bitiş noktası yapılandırması, hizmet bitiş noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="fa8be-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="fa8be-119">İstemci bağlama uygun `securityMode` ve `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="fa8be-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="fa8be-120">Bir çapraz bilgisayar senaryosunda çalışırken, hizmet bitiş noktası adresi buna göre değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="fa8be-121">İstemci uygulaması kullanılacak kullanıcı adını ve parolayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fa8be-121">The client implementation sets the user name and password to use.</span></span>  

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

 <span data-ttu-id="fa8be-122">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fa8be-123">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="fa8be-124">MessageSecurity örneklerine dahil olan Setup.bat toplu iş dosyası, sunucuyu sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili bir sertifikayla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa8be-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="fa8be-125">Toplu iş dosyası iki modda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="fa8be-126">Toplu iş dosyasını tek bilgisayar modunda `setup.bat` çalıştırmak için komut satırına yazın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="fa8be-127">Hizmet modu türünde `setup.bat service`çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="fa8be-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="fa8be-128">Örneği bilgisayarlar da çalıştırırken bu modu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fa8be-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="fa8be-129">Ayrıntılar için bu konunun sonundaki kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="fa8be-130">Aşağıda, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa8be-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="fa8be-131">Sunucu sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa8be-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="fa8be-132">Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fa8be-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="fa8be-133">%SERVER_NAME değişkeni sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="fa8be-134">Sertifika LocalMachine mağazasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="fa8be-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="fa8be-135">Setup.bat toplu iş dosyası bir hizmet bağımsız değişkeni (örneğin) `setup.bat service`ile çalıştırılırsa %SERVER_NAME%bilgisayarın tam nitelikli etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="fa8be-136">Aksi takdirde varsayılan olarak localhost için.</span><span class="sxs-lookup"><span data-stu-id="fa8be-136">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="fa8be-137">Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme</span><span class="sxs-lookup"><span data-stu-id="fa8be-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="fa8be-138">Aşağıdaki satır, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="fa8be-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="fa8be-139">Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="fa8be-140">İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="fa8be-141">Sertifikanın özel anahtarında izin verme</span><span class="sxs-lookup"><span data-stu-id="fa8be-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="fa8be-142">Setup.bat toplu iş dosyasındaki aşağıdaki satırlar, LocalMachine deposunda depolanan sunucu sertifikasını ASP.NET işiçin işiçin hesaba erişebiliyor.</span><span class="sxs-lookup"><span data-stu-id="fa8be-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
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
    > <span data-ttu-id="fa8be-143">Windows'un ABD İngilizce olmayan bir sürümünü kullanıyorsanız, Setup.bat dosyasını düzenlemelisiniz ve `NT AUTHORITY\NETWORK SERVICE` hesap adını bölgesel eşdeğerinizle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fa8be-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fa8be-144">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fa8be-144">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fa8be-145">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa8be-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fa8be-146">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fa8be-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="fa8be-147">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fa8be-147">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="fa8be-148">Yolun Makecert.exe ve FindPrivateKey.exe'nin bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa8be-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2. <span data-ttu-id="fa8be-149">Administrator ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut Komut Ustem komutdosyasındaki örnek yükleme klasöründen Setup.bat'ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-149">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="fa8be-150">Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="fa8be-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fa8be-151">Setup.bat toplu dosyası Visual Studio için Geliştirici Komut Komut Ustem'den çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fa8be-151">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="fa8be-152">Yol ortamı değişkeninin SDK'nın yüklendiği dizine işaret etmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="fa8be-153">Bu ortam değişkeni, Visual Studio için Geliştirici Komut Komut Ustem içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fa8be-153">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="fa8be-154">Adresi `http://localhost/servicemodelsamples/service.svc`girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-154">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>
  
4. <span data-ttu-id="fa8be-155">Client.exe'yi \client\bin'den başlatın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="fa8be-156">İstemci etkinliği istemci konsoluygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-156">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="fa8be-157">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-157">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="fa8be-158">Örneği bilgisayarlarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fa8be-158">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="fa8be-159">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa8be-159">Create a directory on the service computer.</span></span> <span data-ttu-id="fa8be-160">Internet Bilgi Hizmetleri yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa8be-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2. <span data-ttu-id="fa8be-161">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples'ten hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="fa8be-162">\bin alt dizinindeki dosyaları kopyaladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa8be-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="fa8be-163">Ayrıca Setup.bat ve Cleanup.bat dosyalarını servis bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="fa8be-164">İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa8be-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="fa8be-165">İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="fa8be-166">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="fa8be-167">Sunucuda, yönetici `setup.bat service` ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut Komut Ustem'de çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-167">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="fa8be-168">Bağımsız değişkenle birlikte çalışmak, `setup.bat` bilgisayarın tam nitelikli etki alanı adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`</span><span class="sxs-lookup"><span data-stu-id="fa8be-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="fa8be-169">Bilgisayarın tam nitelikli etki alanı adı ile aynı olan yeni sertifika adını (serviceCertificate öğesindeki findValue özniteliğinde) yansıtacak şekilde Web.config'i edin`.`</span><span class="sxs-lookup"><span data-stu-id="fa8be-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7. <span data-ttu-id="fa8be-170">Service.cer dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="fa8be-171">İstemci bilgisayarındaki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fa8be-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="fa8be-172">İstemci de, yönetici ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut Komut Ustem'de ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-172">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="fa8be-173">Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="fa8be-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="fa8be-174">İstemci bilgisayarında, istemci.exe'yi komut isteminden başlatın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="fa8be-175">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="fa8be-176">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="fa8be-176">To clean up after the sample</span></span>  
  
- <span data-ttu-id="fa8be-177">Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa8be-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fa8be-178">Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="fa8be-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="fa8be-179">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa8be-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="fa8be-180">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="fa8be-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
