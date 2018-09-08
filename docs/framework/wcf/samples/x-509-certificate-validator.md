---
title: X.509 Sertifika Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: e54f79046113e5f1a1a1cc065606fd5b706b49ac
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131136"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="70340-102">X.509 Sertifika Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="70340-102">X.509 Certificate Validator</span></span>
<span data-ttu-id="70340-103">Bu örnek bir özel X.509 Sertifika Doğrulayıcı uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="70340-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="70340-104">Bu, yerleşik X.509 Sertifika doğrulama modları hiçbiri uygulama gereksinimlerini için uygun olduğu durumlarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="70340-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="70340-105">Bu örnek, şirket içinde verilen sertifikaları kabul eden özel Doğrulayıcı sağlayıcısı olan bir hizmete gösterir.</span><span class="sxs-lookup"><span data-stu-id="70340-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="70340-106">İstemci hizmete kimlik doğrulaması için bu tür bir sertifika kullanır.</span><span class="sxs-lookup"><span data-stu-id="70340-106">The client uses such a certificate to authenticate to the service.</span></span>  
  
 <span data-ttu-id="70340-107">Herkes kendi kendine verilen bir sertifika oluşturmak gibi Not: hizmet tarafından kullanılan özel Doğrulayıcı ChainTrust X509CertificateValidationMode tarafından sağlanan varsayılan davranışını daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="70340-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="70340-108">Bu güvenlik kapsamı, üretim kodunda bu doğrulama mantığı kullanmadan önce dikkatle düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="70340-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>  
  
 <span data-ttu-id="70340-109">Özet olarak, bu örnek gösterir nasıl:</span><span class="sxs-lookup"><span data-stu-id="70340-109">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="70340-110">İstemci, bir X.509 sertifikası kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="70340-110">The client can be authenticated using an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="70340-111">Sunucu, istemci kimlik bilgileri özel X509CertificateValidator karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="70340-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>  
  
-   <span data-ttu-id="70340-112">Sunucu sunucusunun X.509 sertifikasını kullanarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="70340-112">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="70340-113">Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="70340-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="70340-114">Bir standart yapılandırılmış bağlama `wsHttpBinding` varsayılanları kullanarak `WSSecurity` ve istemci sertifikası kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="70340-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="70340-115">Hizmet davranışı, Doğrulayıcı sınıfını türü ile birlikte istemci X.509 sertifikalarını doğrulamak için özel modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="70340-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="70340-116">Davranış da serviceCertificate öğesini kullanarak sunucu sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70340-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="70340-117">Sunucu sertifikası için aynı değeri içermesi gerekir `SubjectName` olarak `findValue` içinde [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="70340-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
```xml  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use host/baseAddresses to configure base address -->  
        <!-- provided by host -->  
        <host>  
          <baseAddresses>  
            <add baseAddress =  
                "http://localhost:8001/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address specified above, provide one endpoint -->  
        <endpoint address="certificate"  
               binding="wsHttpBinding"  
               bindingConfiguration="Binding"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults ="true"/>  
          <serviceCredentials>  
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
      </system.serviceModel>  
```  
  
 <span data-ttu-id="70340-118">İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin bir yapılandırma adı oluşur.</span><span class="sxs-lookup"><span data-stu-id="70340-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="70340-119">Bağlama istemcinin uygun modu ve şu iletiyle yapılandırıldığı `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="70340-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
        address=  
        "http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
    <bindings>  
        <wsHttpBinding>  
            <!-- X509 certificate binding -->  
            <binding name="Binding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
               </security>  
            </binding>  
       </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- PeerOrChainTrust means that if the certificate -->  
              <!-- is in the user's Trusted People store, then it -->  
              <!-- is trusted without performing a validation of -->  
              <!-- the certificate's issuer chain. -->  
              <!-- This setting is used here for convenience so -->  
              <!-- that the sample can be run without having to -->  
              <!-- have certificates issued by a certification -->  
              <!-- authority (CA). This setting is less secure -->  
              <!-- than the default, ChainTrust. The security -->  
              <!-- implications of this setting should be -->  
              <!-- carefully considered before using -->  
              <!-- PeerOrChainTrust in production code.-->  
              <authentication   
                  certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="70340-120">İstemci uygulaması, istemci sertifikasını kullanmak için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="70340-120">The client implementation sets the client certificate to use.</span></span>  
  
```csharp
// Create a client with Certificate endpoint configuration  
CalculatorClient client = new CalculatorClient("Certificate");  
try  
{  
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    client.Close();  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine("Call timed out : {0}", e.Message);  
    client.Abort();  
}  
catch (CommunicationException e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="70340-121">Bu örnek bir özel X509CertificateValidator sertifikalarını doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="70340-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="70340-122">Öğesinden türetilen CustomX509CertificateValidator, örnek uygulayan <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="70340-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="70340-123">Belgelere bakın <xref:System.IdentityModel.Selectors.X509CertificateValidator> daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="70340-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="70340-124">Bu belirli özel Doğrulayıcı sağlayıcısı örnek, aşağıdaki kodda gösterildiği gibi şirket içinde verilen herhangi bir X.509 sertifikası kabul etmek için Doğrula yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="70340-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>  
  
```csharp
public class CustomX509CertificateValidator : X509CertificateValidator  
{  
  public override void Validate ( X509Certificate2 certificate )  
  {  
   // Only accept self-issued certificates  
   if (certificate.Subject != certificate.Issuer)  
     throw new Exception("Certificate is not self-issued");  
   }  
}  
```  
  
 <span data-ttu-id="70340-125">Doğrulayıcı hizmeti kodunda uygulandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="70340-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="70340-126">Bu yapılır aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="70340-126">This is done using the following code.</span></span>  
  
```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 <span data-ttu-id="70340-127">Ya da aynı şeyi yapılandırmasında şu şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70340-127">Or you can do the same thing in configuration as follows.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
     <behavior name="CalculatorServiceBehavior">  
       ...  
   <serviceCredentials>  
    <!--The serviceCredentials behavior allows one to specify -->   
    <!--authentication constraints on client certificates.-->  
    <clientCertificate>  
    <!-- Setting the certificateValidationMode to Custom means -->   
    <!--that if the custom X509CertificateValidator does NOT -->   
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
    <!--considered before using Custom in production code. -->  
    <authentication certificateValidationMode="Custom"  
       customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />  
   </clientCertificate>  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="70340-128">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="70340-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="70340-129">İstemci başarıyla tüm yöntemlerini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="70340-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="70340-130">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="70340-130">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="70340-131">Kurulum toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="70340-131">Setup Batch File</span></span>  
 <span data-ttu-id="70340-132">Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="70340-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="70340-133">Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="70340-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="70340-134">Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="70340-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="70340-135">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="70340-135">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="70340-136">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70340-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="70340-137">% Sunucu_adı % değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70340-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="70340-138">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="70340-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="70340-139">Localhost varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="70340-139">The default value is localhost.</span></span>  
  
    ```bash  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="70340-140">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:</span><span class="sxs-lookup"><span data-stu-id="70340-140">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="70340-141">İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="70340-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="70340-142">MakeCert.exe tarafından oluşturulan sertifikaları istemci sistem tarafından örtük olarak güvenilmeyen olduğundan bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="70340-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="70340-143">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="70340-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bash  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="70340-144">İstemci sertifikası oluşturma:</span><span class="sxs-lookup"><span data-stu-id="70340-144">Creating the client certificate:</span></span>  
  
     <span data-ttu-id="70340-145">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak istemci sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70340-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="70340-146">% Değişken % USER_NAME istemci adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70340-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="70340-147">Bu istemci kodu arar adı olduğundan, bu değer "test1" için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="70340-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="70340-148">USER_NAME % değerini değiştirirseniz Client.cs kaynak dosyasında karşılık gelen değeri değiştirin ve istemciyi yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70340-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>  
  
     <span data-ttu-id="70340-149">Sertifika CurrentUser depolama konumu altında (Kişisel) My deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="70340-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>  
  
    ```bash  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="70340-150">İstemci sertifikası sunucusunun güvenilen sertifika depolama alanına yükleme:</span><span class="sxs-lookup"><span data-stu-id="70340-150">Installing the client certificate into server's trusted certificate store:</span></span>  
  
     <span data-ttu-id="70340-151">Setup.bat toplu iş dosyasında aşağıdaki satırları istemci sertifikası güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="70340-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="70340-152">MakeCert.exe tarafından oluşturulan sertifikaları sunucu sistem tarafından örtük olarak güvenilmeyen olduğundan bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="70340-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="70340-153">Bir güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — istemci sertifikası ile sunucu sertifika deposuna yerleştirmek, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="70340-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>  
  
    ```bash  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="70340-154">Ayarlama ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="70340-154">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="70340-155">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="70340-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="70340-156">Bir tek - veya çapraz-computerconfiguration içinde örneği çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="70340-156">To run the sample in a single- or cross-computerconfiguration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="70340-157">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="70340-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="70340-158">Setup.bat örnek yükleme klasörü içinde çalıştırılan bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla açılmış.</span><span class="sxs-lookup"><span data-stu-id="70340-158">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="70340-159">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="70340-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="70340-160">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="70340-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="70340-161">İçinde PATH ortam değişkenini ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="70340-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="70340-162">Service.exe service\bin ' başlatın.</span><span class="sxs-lookup"><span data-stu-id="70340-162">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="70340-163">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="70340-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="70340-164">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="70340-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="70340-165">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="70340-165">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="70340-166">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="70340-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="70340-167">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70340-167">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="70340-168">Hizmet program dosyaları \service\bin hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="70340-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="70340-169">Ayrıca hizmet bilgisayara Setup.bat, Cleanup.bat GetComputerName.vbs ve ImportClientCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="70340-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="70340-170">Bir dizin üzerinde istemci computerfor istemci ikili oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70340-170">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="70340-171">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="70340-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="70340-172">Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="70340-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="70340-173">Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="70340-173">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="70340-174">Çalışan `setup.bat` ile `service` bağımsız değişken Service.cer adlı bir dosya için hizmet sertifikası computerand dışarı aktarmaları tam etki alanı adı ile bir hizmet sertifikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="70340-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="70340-175">Yeni sertifika adını yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adıyla aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="70340-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="70340-176">Ayrıca bilgisayar adını değiştirmek \<hizmet > /\<baseAddresses > localhost öğesine hizmet bilgisayarınızın tam adı.</span><span class="sxs-lookup"><span data-stu-id="70340-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="70340-177">Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="70340-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="70340-178">Bir istemcide çalışmasına `setup.bat client` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="70340-178">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="70340-179">Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="70340-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="70340-180">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="70340-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="70340-181">Localhost sunucunun tam etki alanı adıyla değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="70340-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="70340-182">Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="70340-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="70340-183">İstemcide ImportServiceCert.bat yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70340-183">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="70340-184">Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="70340-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="70340-185">Sunucusunda, yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde ImportClientCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70340-185">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="70340-186">Bu istemci sertifikası LocalMachine - TrustedPeople deposu Client.cer dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="70340-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="70340-187">Sunucu bilgisayarında, komut istemi penceresinden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="70340-187">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="70340-188">İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="70340-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="70340-189">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="70340-189">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="70340-190">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="70340-190">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="70340-191">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70340-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="70340-192">Bu, sunucu ve istemci sertifikaları sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="70340-192">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70340-193">Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="70340-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="70340-194">Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun.</span><span class="sxs-lookup"><span data-stu-id="70340-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="70340-195">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="70340-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70340-196">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70340-196">See Also</span></span>
