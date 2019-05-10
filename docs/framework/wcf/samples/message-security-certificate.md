---
title: İleti Güvenliği Sertifikası
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: be9913c5109f86bf54e69beb58c53c4ddc3fd28e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664872"
---
# <a name="message-security-certificate"></a><span data-ttu-id="dbd1c-102">İleti Güvenliği Sertifikası</span><span class="sxs-lookup"><span data-stu-id="dbd1c-102">Message Security Certificate</span></span>
<span data-ttu-id="dbd1c-103">Bu örnek, istemci için X.509 v3 sertifikası kimlik doğrulaması ile WS-güvenlik kullanan ve sunucunun X.509 v3 sertifikası kullanılarak kimlik doğrulaması gerektiren bir uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="dbd1c-104">Bu örnek, tüm uygulama iletileri istemci ve sunucu arasındaki imzalanacak ve şifrelenecek şekilde varsayılan ayarları kullanır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="dbd1c-105">Bu örnek dayanır [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) ve bir istemci konsol programı ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı oluşur.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="dbd1c-106">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbd1c-107">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="dbd1c-108">Örnek denetleme kimlik doğrulaması yapılandırması ve güvenlik bağlamından çağıranının kimliğini edinme aşağıdaki örnek kodda gösterildiği gibi kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

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
  
 <span data-ttu-id="dbd1c-109">Hizmet, hizmet ve hizmetin WSDL belgesinde tanımlanan yapılandırma dosyasında (Web.config) kullanarak WS-MetadataExchange protokolünü kullanarak kullanıma sunmak için bir uç nokta ile iletişim kurmak için bir uç nokta kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="dbd1c-110">Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="dbd1c-111">Bir standart yapılandırılmış bağlama [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ileti güvenliği varsayılan öğe.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="dbd1c-112">Bu örnek ayarlar `clientCredentialType` özniteliği sertifika istemci kimlik doğrulaması isteme.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
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
  
 <span data-ttu-id="dbd1c-113">Davranış hizmeti istemci kimlik doğrulaması kullanılan hizmetin kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="dbd1c-114">Sunucu sertifikası konu adı belirtilen `findValue` özniteliğini [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
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
  
 <span data-ttu-id="dbd1c-115">İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin oluşur.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="dbd1c-116">Bağlama istemci kimlik doğrulama modu ve uygun güvenlik modu ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="dbd1c-117">Bilgisayarlar arası senaryoda çalıştırırken, hizmet uç noktası adresinin uygun şekilde değiştirilir emin olun.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="dbd1c-118">İstemci uygulaması yapılandırma dosyası veya kod yoluyla kullanmak için sertifika ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="dbd1c-119">Aşağıdaki örnek, yapılandırma dosyasında kullanmak üzere sertifikayı ayarlama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="dbd1c-120">Aşağıdaki örnek, programınızda hizmeti çağırmak amacıyla gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="dbd1c-121">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="dbd1c-122">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="dbd1c-123">İle ileti güvenliği örnekleri dahil Setup.bat toplu iş dosyası istemci ve sunucu sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="dbd1c-124">Toplu iş dosyası üç modda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="dbd1c-125">Tek bilgisayarlı modu türü çalıştırılacak **setup.bat** içinde bir geliştirici komut istemi için hizmet modunu türü; Visual Studio için **setup.bat hizmet**; istemci modu türü **setup.bat istemci**.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="dbd1c-126">Örnek bilgisayarlarınızda çalışan istemci ve sunucu modu kullanın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="dbd1c-127">Ayrıntılar için bu konunun sonunda Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="dbd1c-128">Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="dbd1c-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
- <span data-ttu-id="dbd1c-129">İstemci sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="dbd1c-130">Toplu iş dosyasında aşağıdaki satırı, istemci sertifikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="dbd1c-131">Belirtilen istemci adı, oluşturulan sertifikanın konu adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="dbd1c-132">Sertifika depolandığı `My` konumunda depolamak `CurrentUser` depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="dbd1c-133">İstemci sertifikası sunucu güvenilen sertifika depolama alanına yükleme.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="dbd1c-134">Toplu dosya kopyalarını aşağıdaki satırda sunucunun TrustedPeople istemci sertifikayı sunucu ilgili güveni veya no güven kararları yapabilmeleri için depolar.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="dbd1c-135">Bir Windows Communication Foundation (WCF) hizmeti tarafından güvenilmesi için sırayla TrustedPeople depoda yüklü bir sertifika için istemci sertifikası doğrulama modu ayarlamak `PeerOrChainTrust` veya `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="dbd1c-136">Nasıl bu yapılandırma dosyası kullanılarak yapılabilir bilgi edinmek için önceki hizmet yapılandırma örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
- <span data-ttu-id="dbd1c-137">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="dbd1c-138">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="dbd1c-139">% Sunucu_adı % değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="dbd1c-140">Depolanmış bir sertifikayla LocalMachine depolama.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="dbd1c-141">Setup.bat toplu iş dosyasını hizmet bağımsız değişkenlerle çalıştırırsanız (gibi **setup.bat hizmet**) sunucu_adı % bilgisayarın tam etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="dbd1c-142">Aksi takdirde localhost için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-142">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="dbd1c-143">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="dbd1c-144">Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="dbd1c-145">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="dbd1c-146">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="dbd1c-147">Sertifikanın özel anahtarı izin verme.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="dbd1c-148">Aşağıdaki satırları Setup.bat dosyasının erişilebilir LocalMachine deposunda depolanır sunucu sertifikayı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] çalışan işlem hesabı.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
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
    >  <span data-ttu-id="dbd1c-149">ABD dışı kullanıyorsanız Windows İngilizce sürümünü, Setup.bat düzenlemeniz gerekir dosya ve "NT AUTHORITY\NETWORK SERVICE" hesap adı, bölgesel eşdeğerleriyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbd1c-150">Bu toplu iş dosyasında kullanılan araçlar, C:\Program Files\Microsoft Visual Studio 8\Common7\tools veya C:\Program Files\Microsoft SDKs\Windows\v6.0\bin yer alır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="dbd1c-151">Bu dizinlerin uygulamasının sistem yolunuzda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="dbd1c-152">Visual Studio yüklü değilse Visual Studio için geliştirici komut istemi açmak için bu dizin yolunuzda almak için en kolay yolu olan.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="dbd1c-153">Tıklayın **Başlat**ve ardından **tüm programlar**, **Visual Studio 2012**, **Araçları**.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="dbd1c-154">Bu komut istemi zaten yapılandırılmış uygun yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="dbd1c-155">Aksi takdirde, uygun dizin yolunuza el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dbd1c-156">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dbd1c-157">Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:</span><span class="sxs-lookup"><span data-stu-id="dbd1c-157">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dbd1c-158">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dbd1c-159">Bu örnek, şu dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="dbd1c-159">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dbd1c-160">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dbd1c-160">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dbd1c-161">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dbd1c-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="dbd1c-162">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dbd1c-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="dbd1c-163">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="dbd1c-163">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="dbd1c-164">Yönetici ayrıcalıklarıyla Visual Studio için geliştirici komut istemi açın ve örnek yükleme klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="dbd1c-165">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dbd1c-166">Setup.bat toplu iş dosyası, Visual Studio için geliştirici komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="dbd1c-167">Bu, path ortam değişkenine'nın SDK'ın yüklendiği dizini gösterecek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="dbd1c-168">Bu ortam değişkeni, içinde bir geliştirici komut istemi (2010) Visual Studio için otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="dbd1c-169">Adresini girerek bir tarayıcı kullanarak hizmetine erişiminizi doğrulayın `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="dbd1c-170">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="dbd1c-171">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-171">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="dbd1c-172">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="dbd1c-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="dbd1c-173">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="dbd1c-173">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="dbd1c-174">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-174">Create a directory on the service computer.</span></span> <span data-ttu-id="dbd1c-175">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="dbd1c-176">Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="dbd1c-177">Dosyaları \bin alt dizinde kopyalama emin olun.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="dbd1c-178">Ayrıca hizmet bilgisayara Setup.bat Cleanup.bat ve ImportClientCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="dbd1c-179">İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="dbd1c-180">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="dbd1c-181">Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="dbd1c-182">Sunucu üzerinde çalışan **setup.bat hizmet** Geliştirici komut istemini yönetici ayrıcalıklarıyla Visual Studio için.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="dbd1c-183">Çalışan **setup.bat** ile **hizmet** bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="dbd1c-184">Yeni sertifika adını yansıtacak şekilde Web.config'i düzenlemek (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adıyla aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="dbd1c-185">Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="dbd1c-186">Bir istemcide çalışmasına **setup.bat istemci** Geliştirici komut istemini yönetici ayrıcalıklarıyla Visual Studio için.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="dbd1c-187">Çalışan **setup.bat** ile **istemci** bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="dbd1c-188">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="dbd1c-189">Localhost sunucunun tam etki alanı adıyla değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="dbd1c-190">Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="dbd1c-191">İstemcide, yönetici ayrıcalıklarıyla Visual Studio için geliştirici Komut İstemi'nde ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="dbd1c-192">Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="dbd1c-193">Sunucuda, yönetici ayrıcalıklarıyla Visual Studio için geliştirici Komut İstemi'nde ImportClientCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="dbd1c-194">Bu istemci sertifikası LocalMachine - TrustedPeople deposu Client.cer dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="dbd1c-195">İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="dbd1c-196">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="dbd1c-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="dbd1c-197">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="dbd1c-197">To clean up after the sample</span></span>  
  
- <span data-ttu-id="dbd1c-198">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dbd1c-199">Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="dbd1c-200">Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="dbd1c-201">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="dbd1c-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
