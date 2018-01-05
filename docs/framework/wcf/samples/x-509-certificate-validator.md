---
title: "X.509 Sertifika Doğrulayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0717aae2c13c9fa5fcbf0ea47d344cac5675fbea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="c1204-102">X.509 Sertifika Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="c1204-102">X.509 Certificate Validator</span></span>
<span data-ttu-id="c1204-103">Bu örnek, özel bir X.509 Sertifika Doğrulayıcı uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c1204-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="c1204-104">Bu, yerleşik X.509 Sertifika doğrulama modları hiçbiri uygulama gereksinimleri için uygun olduğu durumlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c1204-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="c1204-105">Bu örnekte kendi kendine verilen sertifikaların kabul özel bir doğrulayıcı sahip bir hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c1204-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="c1204-106">İstemci, bir hizmetin kimliğini bu tür bir sertifika kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1204-106">The client uses such a certificate to authenticate to the service.</span></span>  
  
 <span data-ttu-id="c1204-107">Not: herhangi bir kendi kendine sertifikayı oluşturabileceğiniz gibi hizmeti tarafından kullanılan özel Doğrulayıcı ChainTrust X509CertificateValidationMode tarafından sağlanan varsayılan davranışı daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="c1204-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="c1204-108">Bu güvenlik uygulamalarını, üretim kodunda bu doğrulama mantığını kullanmadan önce dikkatle düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="c1204-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>  
  
 <span data-ttu-id="c1204-109">Bu örnek özetinde gösterir nasıl:</span><span class="sxs-lookup"><span data-stu-id="c1204-109">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="c1204-110">İstemci, bir X.509 sertifikası kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c1204-110">The client can be authenticated using an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="c1204-111">Sunucu, istemci kimlik bilgileri özel X509CertificateValidator karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="c1204-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>  
  
-   <span data-ttu-id="c1204-112">Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="c1204-112">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="c1204-113">Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="c1204-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="c1204-114">Bağlama ile standart bir yapılandırılmış `wsHttpBinding` , varsayılan olarak kullanmaya `WSSecurity` ve istemci sertifikası kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c1204-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="c1204-115">Hizmet davranışı Doğrulayıcı sınıfını türü ile birlikte istemci X.509 sertifikalarını doğrularken için özel modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1204-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="c1204-116">Davranış da serviceCertificate öğesi kullanarak sunucu sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1204-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="c1204-117">Sunucu sertifikası için aynı değeri içermesi gerekir `SubjectName` olarak `findValue` içinde [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="c1204-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="c1204-118">Yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="c1204-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="c1204-119">Bağlama istemcinin uygun modunu ve ileti yapılandırıldığı `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="c1204-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="c1204-120">İstemci uygulaması istemci sertifikası kullanacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c1204-120">The client implementation sets the client certificate to use.</span></span>  
  
```  
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
  
 <span data-ttu-id="c1204-121">Bu örnek özel X509CertificateValidator sertifikalarını doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1204-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="c1204-122">Örnek türetilmiş CustomX509CertificateValidator uygulayan <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="c1204-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="c1204-123">Belgelerine bakın <xref:System.IdentityModel.Selectors.X509CertificateValidator> daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c1204-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="c1204-124">Bu belirli özel Doğrulayıcı örnek aşağıdaki kodda gösterildiği gibi kendi kendine verilen herhangi bir X.509 sertifikayı kabul etmek için Doğrula yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="c1204-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="c1204-125">Doğrulayıcı hizmet kodunda tamamlandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgi sahibi olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1204-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="c1204-126">Bu yapılır aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="c1204-126">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 <span data-ttu-id="c1204-127">Veya yapılandırma aynı şeyi şu şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1204-127">Or you can do the same thing in configuration as follows.</span></span>  
  
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
  
 <span data-ttu-id="c1204-128">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c1204-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c1204-129">İstemci, başarıyla tüm yöntemleri çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1204-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="c1204-130">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c1204-130">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="c1204-131">Toplu iş dosyası Kurulumu</span><span class="sxs-lookup"><span data-stu-id="c1204-131">Setup Batch File</span></span>  
 <span data-ttu-id="c1204-132">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1204-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="c1204-133">Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1204-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="c1204-134">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="c1204-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="c1204-135">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="c1204-135">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="c1204-136">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1204-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="c1204-137">% Sunucu_adı % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1204-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="c1204-138">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c1204-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="c1204-139">Localhost varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="c1204-139">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="c1204-140">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="c1204-140">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="c1204-141">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="c1204-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="c1204-142">MakeCert.exe tarafından oluşturulan sertifikaları istemci sistem tarafından dolaylı olarak güvenilmeyen olduğundan bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c1204-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="c1204-143">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c1204-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="c1204-144">İstemci sertifikası oluşturma:</span><span class="sxs-lookup"><span data-stu-id="c1204-144">Creating the client certificate:</span></span>  
  
     <span data-ttu-id="c1204-145">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak istemci sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1204-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="c1204-146">% USER_NAME % değişkeni istemci adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1204-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="c1204-147">Bu istemci kodu arar adı olduğu için bu değer "test1" ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c1204-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="c1204-148">USER_NAME % değerini değiştirirseniz Client.cs kaynak dosyası içinde karşılık gelen değerle değiştirin ve istemci yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1204-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>  
  
     <span data-ttu-id="c1204-149">Sertifika Currentuser'a depolama konumu altında (Kişisel) My deposunda saklanır.</span><span class="sxs-lookup"><span data-stu-id="c1204-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="c1204-150">İstemci sertifikası sunucunun güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="c1204-150">Installing the client certificate into server's trusted certificate store:</span></span>  
  
     <span data-ttu-id="c1204-151">Setup.bat toplu iş dosyası aşağıdaki satırları istemci sertifikası güvenilir Kişiler deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1204-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="c1204-152">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak sunucu sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c1204-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="c1204-153">Bir güvenilen kök sertifika kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — istemci sertifikası ile sunucu sertifika depolama doldurma, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c1204-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="c1204-154">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1204-154">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="c1204-155">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c1204-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="c1204-156">Bir tek - veya çapraz-computerconfiguration içinde örneği çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1204-156">To run the sample in a single- or cross-computerconfiguration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="c1204-157">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c1204-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="c1204-158">İçinde örnek yükleme klasöründen Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla açılır.</span><span class="sxs-lookup"><span data-stu-id="c1204-158">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="c1204-159">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="c1204-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c1204-160">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="c1204-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="c1204-161">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="c1204-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="c1204-162">Service.exe service\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="c1204-162">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="c1204-163">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="c1204-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="c1204-164">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c1204-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="c1204-165">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="c1204-165">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c1204-166">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c1204-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="c1204-167">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1204-167">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="c1204-168">Hizmet program dosyalarını \service\bin hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1204-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="c1204-169">Ayrıca Setup.bat, Cleanup.bat, GetComputerName.vbs ve ImportClientCert.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1204-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="c1204-170">Bir dizin üzerinde istemci computerfor istemci ikili dosyalarının oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1204-170">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="c1204-171">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1204-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="c1204-172">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1204-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="c1204-173">Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="c1204-173">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="c1204-174">Çalışan `setup.bat` ile `service` bağımsız değişkeni computerand dışarı tam etki alanı adı ile bir hizmet sertifikası Service.cer adlı bir dosyaya hizmet sertifikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1204-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="c1204-175">Yeni sertifika yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adı ile aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="c1204-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="c1204-176">Ayrıca bilgisayar adını değiştirme \<hizmet > /\<baseAddresses > localhost öğesine hizmet bilgisayarınızı tam adı.</span><span class="sxs-lookup"><span data-stu-id="c1204-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="c1204-177">Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1204-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="c1204-178">İstemci üzerinde çalışan `setup.bat client` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="c1204-178">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="c1204-179">Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="c1204-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="c1204-180">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c1204-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="c1204-181">Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="c1204-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="c1204-182">Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1204-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="c1204-183">İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1204-183">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="c1204-184">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="c1204-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="c1204-185">Sunucu üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportClientCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1204-185">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="c1204-186">Bu istemci sertifikası LocalMachine - TrustedPeople deposunda Client.cer dosyadan alır.</span><span class="sxs-lookup"><span data-stu-id="c1204-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="c1204-187">Sunucu bilgisayarda komut istemi penceresinden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="c1204-187">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="c1204-188">İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="c1204-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="c1204-189">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="c1204-189">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c1204-190">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="c1204-190">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="c1204-191">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1204-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="c1204-192">Bu sunucu ve istemci sertifikaları sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c1204-192">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1204-193">Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="c1204-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="c1204-194">Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="c1204-194">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c1204-195">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c1204-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1204-196">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1204-196">See Also</span></span>
