---
title: "İleti Güvenliği Sertifikası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
caps.latest.revision: "51"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d21bda439e40880a389ccbb9bb28a45a16735805
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-certificate"></a><span data-ttu-id="1d178-102">İleti Güvenliği Sertifikası</span><span class="sxs-lookup"><span data-stu-id="1d178-102">Message Security Certificate</span></span>
<span data-ttu-id="1d178-103">Bu örnek, istemci için X.509 v3 sertifikası kimlik doğrulaması ile WS güvenliği kullanan ve sunucunun X.509 v3 sertifikası kullanılarak kimlik doğrulaması gerektiren bir uygulama uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d178-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="1d178-104">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir, bu örnek varsayılan ayarları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1d178-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="1d178-105">Bu örnek dayanır [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) ve bir istemci konsol programı ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d178-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="1d178-106">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="1d178-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d178-107">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="1d178-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1d178-108">Örnek, yapılandırma ve güvenlik bağlamından çağıranının kimliğini edinme aşağıdaki örnek kodda gösterildiği gibi kullanarak denetleme kimlik doğrulaması gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d178-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="1d178-109">Hizmetin hizmet ve yapılandırma dosyasında (Web.config) kullanılarak tanımlanmış WS-MetadataExchange protokolünü kullanarak hizmetin WSDL belgesi gösterme için bir uç noktası ile iletişim için bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="1d178-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="1d178-110">Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d178-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="1d178-111">Bağlama ile standart bir yapılandırılmış [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ileti güvenliği için kullanılacak varsayılan olarak öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d178-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="1d178-112">Bu örnek ayarlar `clientCredentialType` özniteliği için istemci kimlik doğrulaması istemek için sertifika.</span><span class="sxs-lookup"><span data-stu-id="1d178-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
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
  
 <span data-ttu-id="1d178-113">Davranış istemci hizmeti doğruladığında kullanılan hizmetin kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d178-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="1d178-114">Sunucu sertifikası konu adı belirtilen `findValue` özniteliğini [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d178-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
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
  
 <span data-ttu-id="1d178-115">Hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d178-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="1d178-116">Bağlama istemci kimlik doğrulama modu ve uygun güvenlik modu ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="1d178-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="1d178-117">Bilgisayarlar arası senaryoda çalıştırırken, hizmet uç noktası adresi buna göre değişir emin olun.</span><span class="sxs-lookup"><span data-stu-id="1d178-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="1d178-118">İstemci uygulaması, yapılandırma dosyası veya kod aracılığıyla kullanmak üzere sertifika ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d178-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="1d178-119">Aşağıdaki örnek yapılandırma dosyasında kullanmak üzere sertifikayı nasıl kurulur gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d178-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="1d178-120">Aşağıdaki örnek, programınıza hizmeti çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d178-120">The following sample shows how to call the service in your program.</span></span>  
  
```  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 <span data-ttu-id="1d178-121">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d178-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1d178-122">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1d178-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="1d178-123">İleti güvenliği örnekleriyle dahil Setup.bat toplu iş dosyası, istemci ve sunucu ile ilgili sertifikalar sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="1d178-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="1d178-124">Toplu iş dosyası üç modda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d178-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="1d178-125">Tek bilgisayar modu türü çalıştırmak için **setup.bat** hizmet modu türü için bir Visual Studio komut istemi içinde; **setup.bat hizmet**; ve istemci modu türü için **setup.bat istemci** .</span><span class="sxs-lookup"><span data-stu-id="1d178-125">To run in single-computer mode type **setup.bat** in a Visual Studio Command Prompt ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="1d178-126">İstemci ve sunucu modu örnek bilgisayarlar arasında çalıştırırken kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d178-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="1d178-127">Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="1d178-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="1d178-128">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="1d178-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
-   <span data-ttu-id="1d178-129">İstemci sertifikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="1d178-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="1d178-130">Toplu iş dosyasında aşağıdaki satırı istemci sertifikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1d178-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="1d178-131">Belirtilen istemci adı oluşturulan sertifika konu adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d178-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="1d178-132">Sertifika depolandığı `My` adresindeki depolamak `CurrentUser` depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="1d178-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="1d178-133">İstemci sertifikası, sunucu güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="1d178-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="1d178-134">Toplu dosya kopyalarını aşağıdaki satırda sunucunun TrustedPeople içine istemci sertifikası sunucu ilgili güven veya no güven kararları yapabilmek depolar.</span><span class="sxs-lookup"><span data-stu-id="1d178-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="1d178-135">Tarafından güvenilmesi sırada TrustedPeople deposunda yüklü bir sertifika için bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti, istemci sertifikası doğrulama modunu ayarlanmalıdır `PeerOrChainTrust` veya `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="1d178-135">In order for a certificate installed in the TrustedPeople store to be trusted by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="1d178-136">Önceki hizmet yapılandırma örneği nasıl bu yapılandırma dosyası kullanarak yapılabilir bilgi edinmek için bkz.</span><span class="sxs-lookup"><span data-stu-id="1d178-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
-   <span data-ttu-id="1d178-137">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1d178-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="1d178-138">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1d178-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="1d178-139">% Sunucu_adı % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d178-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="1d178-140">Sertifika saklanır LocalMachine deposundaki.</span><span class="sxs-lookup"><span data-stu-id="1d178-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="1d178-141">Bir hizmet bağımsız değişkeniyle Setup.bat toplu iş dosyası çalıştırırsanız (gibi **setup.bat hizmet**) sunucu_adı % bilgisayarın tam etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="1d178-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="1d178-142">Aksi takdirde localhost için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="1d178-142">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="1d178-143">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="1d178-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="1d178-144">Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="1d178-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1d178-145">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1d178-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1d178-146">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1d178-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="1d178-147">Sertifikanın özel anahtarı izin verme.</span><span class="sxs-lookup"><span data-stu-id="1d178-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="1d178-148">Erişilebilir LocalMachine deposundaki depolanan sunucu sertifikası Setup.bat dosyası aşağıdaki satırları olun [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] çalışan işlem hesabı.</span><span class="sxs-lookup"><span data-stu-id="1d178-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
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
    >  <span data-ttu-id="1d178-149">ABD dışındaki kullanıyorsanız Windows İngilizce sürümünü, Setup.bat düzenlemeniz gerekir dosya ve "NT AUTHORITY\NETWORK SERVICE" hesap adı, bölgesel eşdeğerleriyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1d178-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d178-150">Bu toplu iş dosyasında kullanılan araçlar, C:\Program Files\Microsoft Visual Studio 8\Common7\tools veya C:\Program Files\Microsoft SDKs\Windows\v6.0\bin bulunur.</span><span class="sxs-lookup"><span data-stu-id="1d178-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="1d178-151">Bu dizinleri, sistem yolunda biri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d178-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="1d178-152">Visual Studio yüklüyse, Visual Studio komut istemi açmak için bu dizin yolunuzda almak için en kolay yolu olan.</span><span class="sxs-lookup"><span data-stu-id="1d178-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Visual Studio Command Prompt.</span></span> <span data-ttu-id="1d178-153">Tıklatın **Başlat**ve ardından **tüm programlar**, **Visual Studio 2012**, **Araçları**.</span><span class="sxs-lookup"><span data-stu-id="1d178-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="1d178-154">Bu komut istemi zaten yapılandırılmış uygun yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="1d178-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="1d178-155">Aksi takdirde, uygun dizin yolunu el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d178-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d178-156">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="1d178-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1d178-157">Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:</span><span class="sxs-lookup"><span data-stu-id="1d178-157">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1d178-158">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1d178-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1d178-159">Bu örnek aşağıdaki dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="1d178-159">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1d178-160">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="1d178-160">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1d178-161">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1d178-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1d178-162">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1d178-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="1d178-163">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1d178-163">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="1d178-164">Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve Setup.bat örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1d178-164">Open a Visual Studio Command Prompt  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="1d178-165">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="1d178-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d178-166">Setup.bat toplu iş dosyası, Visual Studio komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1d178-166">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt .</span></span> <span data-ttu-id="1d178-167">Path ortam değişkeni SDK yüklendiği dizinine işaret etmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d178-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="1d178-168">Bu ortam değişkenine bir Visual Studio komut istemi içinde (2010) otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1d178-168">This environment variable is automatically set within a Visual Studio Command Prompt (2010).</span></span>  
  
2.  <span data-ttu-id="1d178-169">Hizmeti adresini girerek bir tarayıcı kullanarak erişimi doğrulamak `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="1d178-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3.  <span data-ttu-id="1d178-170">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="1d178-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="1d178-171">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d178-171">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="1d178-172">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="1d178-172">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1d178-173">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1d178-173">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="1d178-174">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1d178-174">Create a directory on the service computer.</span></span> <span data-ttu-id="1d178-175">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1d178-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="1d178-176">Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1d178-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="1d178-177">\Bin alt dizinindeki dosyaları kopyalayın emin olun.</span><span class="sxs-lookup"><span data-stu-id="1d178-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="1d178-178">Ayrıca Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1d178-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="1d178-179">İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1d178-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="1d178-180">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1d178-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="1d178-181">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1d178-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="1d178-182">Sunucu üzerinde çalışan **setup.bat hizmet** yönetici ayrıcalıklarına sahip bir Visual Studio komut istemindeki.</span><span class="sxs-lookup"><span data-stu-id="1d178-182">On the server, run **setup.bat service** in a Visual Studio command prompt with administrator privileges.</span></span> <span data-ttu-id="1d178-183">Çalışan **setup.bat** ile **hizmet** bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="1d178-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="1d178-184">Web.config dosyasını yeni sertifika yansıtacak şekilde düzenleyin (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adı ile aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="1d178-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="1d178-185">Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1d178-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="1d178-186">İstemci üzerinde çalışan **setup.bat istemci** yönetici ayrıcalıklarına sahip bir Visual Studio komut istemindeki.</span><span class="sxs-lookup"><span data-stu-id="1d178-186">On the client, run **setup.bat client** in a Visual Studio command prompt with administrator privileges.</span></span> <span data-ttu-id="1d178-187">Çalışan **setup.bat** ile **istemci** bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="1d178-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="1d178-188">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1d178-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="1d178-189">Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="1d178-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="1d178-190">Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1d178-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="1d178-191">İstemcide ImportServiceCert.bat Visual Studio komut istemini yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1d178-191">On the client, run ImportServiceCert.bat in a Visual Studio command prompt with administrative privileges.</span></span> <span data-ttu-id="1d178-192">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="1d178-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="1d178-193">Sunucu üzerinde ImportClientCert.bat Visual Studio komut istemini yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1d178-193">On the server, run ImportClientCert.bat in a Visual Studio command prompt with administrative privileges.</span></span> <span data-ttu-id="1d178-194">Bu istemci sertifikası LocalMachine - TrustedPeople deposunda Client.cer dosyadan alır.</span><span class="sxs-lookup"><span data-stu-id="1d178-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="1d178-195">İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="1d178-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="1d178-196">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="1d178-196">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="1d178-197">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="1d178-197">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="1d178-198">Örnek çalıştıran bitirdikten sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1d178-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d178-199">Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="1d178-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="1d178-200">Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="1d178-200">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="1d178-201">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="1d178-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d178-202">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d178-202">See Also</span></span>
