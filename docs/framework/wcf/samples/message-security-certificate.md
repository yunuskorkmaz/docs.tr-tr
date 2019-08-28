---
title: İleti Güvenliği Sertifikası
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 496589a0c1a5a0a029e464bfdd87caf8515bb9e3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044876"
---
# <a name="message-security-certificate"></a><span data-ttu-id="89d98-102">İleti Güvenliği Sertifikası</span><span class="sxs-lookup"><span data-stu-id="89d98-102">Message Security Certificate</span></span>
<span data-ttu-id="89d98-103">Bu örnek, istemci için X. 509.440 v3 sertifika kimlik doğrulamasıyla WS-Security kullanan bir uygulamanın nasıl uygulanacağını gösterir ve sunucunun X. 509.440 v3 sertifikasını kullanarak sunucu kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="89d98-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="89d98-104">Bu örnek, istemci ve sunucu arasındaki tüm uygulama iletilerinin imzalanıp şifrelendiğinden emin olmak için varsayılan ayarları kullanır.</span><span class="sxs-lookup"><span data-stu-id="89d98-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="89d98-105">Bu örnek, [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) 'i temel alır ve Internet INFORMATION SERVICES (IIS) tarafından barındırılan bir istemci konsol programından ve bir hizmet kitaplığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="89d98-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="89d98-106">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="89d98-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89d98-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="89d98-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="89d98-108">Örnek, aşağıdaki örnek kodda gösterildiği gibi, yapılandırma ve arayanın kimliğini güvenlik bağlamdan alma ' yı kullanarak, kimlik doğrulamasının denetlenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="89d98-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="89d98-109">Hizmet, hizmet ile iletişim kurmak için bir uç nokta ve yapılandırma dosyası (Web. config) kullanılarak tanımlanan WS-MetadataExchange protokolünü kullanarak hizmetin WSDL belgesini açığa çıkarmak için bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="89d98-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="89d98-110">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="89d98-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="89d98-111">Bağlama, varsayılan olarak ileti güvenliğini kullanan standart [ \<bir WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="89d98-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="89d98-112">Bu örnek, `clientCredentialType` istemci kimlik doğrulaması gerektirmek için özniteliğini sertifikaya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="89d98-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="89d98-113">Davranış, istemci hizmetin kimliğini doğruladığında kullanılan hizmetin kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89d98-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="89d98-114">Sunucu sertifikası konu adı, `findValue` [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) öğesindeki özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="89d98-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="89d98-115">İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="89d98-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="89d98-116">İstemci bağlama, uygun güvenlik modu ve kimlik doğrulama moduyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="89d98-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="89d98-117">Bir çapraz bilgisayar senaryosunda çalışırken, hizmet uç noktası adresinin uygun şekilde değiştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="89d98-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="89d98-118">İstemci uygulama, yapılandırma dosyası ya da kod aracılığıyla sertifikayı kullanacak şekilde ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="89d98-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="89d98-119">Aşağıdaki örnek, yapılandırma dosyasında kullanılmak üzere sertifikanın nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89d98-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="89d98-120">Aşağıdaki örnek, programınızda hizmetin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89d98-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="89d98-121">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="89d98-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="89d98-122">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="89d98-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="89d98-123">Ileti güvenlik örneklerine eklenen Setup. bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren bir barındırılan uygulamayı çalıştırmak için istemciyi ve sunucuyu ilgili sertifikalarla yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="89d98-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="89d98-124">Toplu iş dosyası üç modda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="89d98-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="89d98-125">Visual Studio için Geliştirici Komut İstemi, tek bilgisayarlı modda çalıştırmak için **Setup. bat** yazın; hizmet modu için **Setup. bat hizmeti**; istemci modu için **Setup. bat client**yazın.</span><span class="sxs-lookup"><span data-stu-id="89d98-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="89d98-126">Örneği bilgisayarlar arasında çalıştırırken istemci ve sunucu modunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="89d98-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="89d98-127">Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="89d98-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="89d98-128">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="89d98-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
- <span data-ttu-id="89d98-129">İstemci sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="89d98-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="89d98-130">Toplu iş dosyasındaki aşağıdaki satır, istemci sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89d98-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="89d98-131">Belirtilen istemci adı, oluşturulan sertifikanın konu adı ' nda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89d98-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="89d98-132">Sertifika mağaza konumunda mağaza `My` `CurrentUser` 'da depolanır.</span><span class="sxs-lookup"><span data-stu-id="89d98-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="89d98-133">İstemci sertifikası sunucunun Güvenilen sertifika deposuna yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="89d98-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="89d98-134">Toplu iş dosyasında aşağıdaki satır, sunucunun ilgili güveni veya güven dışı kararlar verebilmeleri için istemci sertifikasını sunucunun Trustedkişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="89d98-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="89d98-135">Trustedkişiler deposuna yüklenmiş bir sertifikanın bir Windows Communication Foundation (WCF) hizmeti tarafından güvenilmesi için, istemci sertifikası doğrulama modunun veya `PeerOrChainTrust` `PeerTrust`olarak ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="89d98-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="89d98-136">Bunun bir yapılandırma dosyası kullanılarak nasıl yapılabileceğinizi öğrenmek için önceki hizmet yapılandırma örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="89d98-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
- <span data-ttu-id="89d98-137">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="89d98-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="89d98-138">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89d98-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="89d98-139">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="89d98-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="89d98-140">Sertifika, LocalMachine deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="89d98-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="89d98-141">Setup. bat toplu iş dosyası bir hizmet bağımsız değişkeniyle (örneğin, **Setup. bat hizmeti**) ÇALıŞıYORSA% sunucu_adı% bilgisayarın tam etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="89d98-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="89d98-142">Aksi takdirde, varsayılan olarak localhost olur.</span><span class="sxs-lookup"><span data-stu-id="89d98-142">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="89d98-143">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="89d98-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="89d98-144">Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="89d98-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="89d98-145">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89d98-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="89d98-146">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="89d98-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="89d98-147">Sertifikanın özel anahtarına izin veriliyor.</span><span class="sxs-lookup"><span data-stu-id="89d98-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="89d98-148">Setup. bat dosyasındaki aşağıdaki satırlar, LocalMachine deposunda depolanan sunucu sertifikasını ASP.NET çalışan işlem hesabına erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="89d98-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
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
    > <span data-ttu-id="89d98-149">U-U olmayan bir. S kullanıyorsanız. Windows 'un İngilizce sürümü olan Setup. bat dosyasını düzenlemeniz ve "NT AUTHORITY\NETWORK SERVICE" hesap adını bölge eşdeğeriyle değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89d98-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89d98-150">Bu toplu iş dosyasında kullanılan araçlar C:\Program Files\Microsoft Visual Studio 8 \ Common7\tools veya C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="89d98-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="89d98-151">Bu dizinlerden biri sistem yolunuzda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89d98-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="89d98-152">Visual Studio yüklüyse, yolunuzda bu dizini almanın en kolay yolu Visual Studio için Geliştirici Komut İstemi açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89d98-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="89d98-153">**Başlat**' a tıklayın ve ardından **tüm programlar**, **Visual Studio 2012**, **Araçlar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="89d98-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="89d98-154">Bu komut isteminde uygun yollar zaten yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="89d98-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="89d98-155">Aksi takdirde, uygun dizini yolunuza el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89d98-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="89d98-156">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="89d98-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="89d98-157">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin:</span><span class="sxs-lookup"><span data-stu-id="89d98-157">Check for the following (default) directory before continuing:</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="89d98-158">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="89d98-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="89d98-159">Bu örnek aşağıdaki dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="89d98-159">This sample is located in the following directory:</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="89d98-160">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="89d98-160">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="89d98-161">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="89d98-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="89d98-162">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="89d98-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="89d98-163">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="89d98-163">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="89d98-164">Yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve örnek yükleme klasöründen Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89d98-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="89d98-165">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="89d98-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="89d98-166">Setup. bat toplu iş dosyası, Visual Studio için Geliştirici Komut İstemi çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="89d98-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="89d98-167">PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="89d98-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="89d98-168">Bu ortam değişkeni, Visual Studio için bir Geliştirici Komut İstemi içinde otomatik olarak ayarlanır (2010).</span><span class="sxs-lookup"><span data-stu-id="89d98-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="89d98-169">Adresi `http://localhost/servicemodelsamples/service.svc`girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="89d98-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="89d98-170">\Client\bin. adresinden Client. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="89d98-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="89d98-171">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="89d98-171">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="89d98-172">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="89d98-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="89d98-173">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="89d98-173">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="89d98-174">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89d98-174">Create a directory on the service computer.</span></span> <span data-ttu-id="89d98-175">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89d98-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="89d98-176">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89d98-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="89d98-177">Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="89d98-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="89d98-178">Ayrıca Setup. bat, Cleanup. bat ve ImportClientCert. bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89d98-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="89d98-179">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89d98-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="89d98-180">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89d98-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="89d98-181">Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89d98-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="89d98-182">Sunucusunda, yönetici ayrıcalıklarına sahip bir Visual Studio için Geliştirici Komut İstemi **Setup. bat hizmetini** çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89d98-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="89d98-183">**Setup. bat** dosyasını **hizmet** bağımsız değişkeniyle çalıştırmak, bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="89d98-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="89d98-184">Web. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni `findValue` sertifika adını ( [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="89d98-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="89d98-185">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89d98-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="89d98-186">İstemcisinde, yönetici ayrıcalıklarına sahip bir Visual Studio için Geliştirici Komut İstemi **Setup. bat istemcisini** çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89d98-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="89d98-187">**Setup. bat** dosyasını **istemci** bağımsız değişkeniyle çalıştırmak, Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="89d98-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="89d98-188">İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="89d98-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="89d98-189">Localhost 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="89d98-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="89d98-190">Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89d98-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="89d98-191">İstemcisinde, yönetim ayrıcalıklarına sahip bir Visual Studio için Geliştirici Komut İstemi ImportServiceCert. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89d98-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="89d98-192">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="89d98-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="89d98-193">Sunucusunda, yönetim ayrıcalıklarına sahip bir Visual Studio için Geliştirici Komut İstemi ImportClientCert. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89d98-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="89d98-194">Bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="89d98-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="89d98-195">İstemci bilgisayarda, bir komut istemi penceresinden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="89d98-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="89d98-196">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="89d98-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="89d98-197">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="89d98-197">To clean up after the sample</span></span>  
  
- <span data-ttu-id="89d98-198">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89d98-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="89d98-199">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="89d98-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="89d98-200">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="89d98-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="89d98-201">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="89d98-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
