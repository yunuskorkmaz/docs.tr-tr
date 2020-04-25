---
title: X.509 Sertifika Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: ba73381bb6211dcbd1ddad1457f9ae8611008d43
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141208"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="92f9c-102">X.509 Sertifika Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="92f9c-102">X.509 Certificate Validator</span></span>

<span data-ttu-id="92f9c-103">Bu örnek, özel bir X. 509.440 sertifika Doğrulayıcısı nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="92f9c-104">Bu, yerleşik X. 509.440 sertifika doğrulama modlarının hiçbirinin uygulamanın gereksinimlerine uygun olmadığı durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="92f9c-105">Bu örnek, kendine verilen sertifikaları kabul eden özel bir doğrulayıcısı olan bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="92f9c-106">İstemci, hizmette kimlik doğrulaması yapmak için bu sertifikayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-106">The client uses such a certificate to authenticate to the service.</span></span>

<span data-ttu-id="92f9c-107">Note: herkes kendi kendine verilen bir sertifika yapılandırabileceğinden, hizmet tarafından kullanılan özel Doğrulayıcı, ChainTrust X509CertificateValidationMode tarafından sağlanmış olan varsayılan davranıştan daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="92f9c-108">Bu doğrulama mantığı üretim kodunda kullanılmadan önce bunun güvenlik açısından olumsuz bir şekilde ele alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

<span data-ttu-id="92f9c-109">Özet bölümünde bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="92f9c-109">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="92f9c-110">İstemcinin kimliği bir X. 509.440 sertifikası kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-110">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="92f9c-111">Sunucu, istemci kimlik bilgilerini özel bir X509CertificateValidator karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="92f9c-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="92f9c-112">Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-112">The server is authenticated using the server's X.509 certificate.</span></span>

<span data-ttu-id="92f9c-113">Hizmet, App. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="92f9c-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="92f9c-114">Bağlama, varsayılan olarak ve istemci sertifikası `wsHttpBinding` kimlik doğrulamasını kullanan `WSSecurity` bir standart ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="92f9c-115">Hizmet davranışı, istemci X. 509.440 sertifikalarını doğrulama sınıfının türüyle birlikte doğrulamak için özel modu belirtir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="92f9c-116">Davranış, serviceCertificate öğesini kullanarak sunucu sertifikasını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="92f9c-117">Sunucu sertifikasının, `SubjectName` [ \<ServiceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)için `findValue` aynı değeri içermesi vardır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

<span data-ttu-id="92f9c-118">İstemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="92f9c-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="92f9c-119">İstemci bağlama uygun mod ve iletiyle `clientCredentialType`yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

<span data-ttu-id="92f9c-120">İstemci uygulama, kullanılacak istemci sertifikasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="92f9c-120">The client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="92f9c-121">Bu örnek, sertifikaları doğrulamak için özel bir X509CertificateValidator kullanır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="92f9c-122">Örnek, öğesinden <xref:System.IdentityModel.Selectors.X509CertificateValidator>türetilmiş CustomX509CertificateValidator uygular.</span><span class="sxs-lookup"><span data-stu-id="92f9c-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="92f9c-123">Daha fazla bilgi <xref:System.IdentityModel.Selectors.X509CertificateValidator> için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="92f9c-124">Bu özel Doğrulayıcı örneği, aşağıdaki kodda gösterildiği gibi kendi kendine yayınlanan herhangi bir X. 509.952 sertifikasını kabul etmek için Validate metodunu uygular.</span><span class="sxs-lookup"><span data-stu-id="92f9c-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

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

 <span data-ttu-id="92f9c-125">Doğrulayıcı hizmet koduna uygulandıktan sonra, hizmet ana bilgisayarının kullanılacak Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="92f9c-126">Bu, aşağıdaki kod kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-126">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="92f9c-127">Ya da yapılandırma ile aynı şeyi aşağıdaki şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92f9c-127">Or you can do the same thing in configuration as follows.</span></span>

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
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="92f9c-128">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="92f9c-129">İstemci tüm yöntemleri başarıyla çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="92f9c-130">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-130">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="92f9c-131">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="92f9c-131">Setup Batch File</span></span>

<span data-ttu-id="92f9c-132">Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="92f9c-133">Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="92f9c-134">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sunar:</span><span class="sxs-lookup"><span data-stu-id="92f9c-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="92f9c-135">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="92f9c-135">Creating the server certificate:</span></span>

     <span data-ttu-id="92f9c-136">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="92f9c-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="92f9c-137">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="92f9c-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="92f9c-138">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="92f9c-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="92f9c-139">Varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="92f9c-139">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="92f9c-140">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="92f9c-140">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="92f9c-141">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="92f9c-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="92f9c-142">MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="92f9c-143">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="92f9c-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="92f9c-144">İstemci sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="92f9c-144">Creating the client certificate:</span></span>

     <span data-ttu-id="92f9c-145">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak istemci sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="92f9c-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="92f9c-146">% USER_NAME% değişkeni istemci adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="92f9c-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="92f9c-147">Bu değer "test1" olarak ayarlanır çünkü bu, istemci kodunun aradığı addır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="92f9c-148">% USER_NAME değerini değiştirirseniz, Client.cs kaynak dosyasında karşılık gelen değeri değiştirmeniz ve istemciyi yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="92f9c-149">Sertifika, CurrentUser Store konumu altında (kişisel) deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="92f9c-150">İstemci sertifikasını sunucunun Güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="92f9c-150">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="92f9c-151">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, istemci sertifikasını güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="92f9c-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="92f9c-152">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların sunucu sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="92f9c-153">Güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), sunucu sertifika deposunu istemci sertifikası ile doldurmak için bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="92f9c-154">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="92f9c-154">To set up and build the sample</span></span>

1. <span data-ttu-id="92f9c-155">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="92f9c-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="92f9c-156">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-156">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="92f9c-157">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="92f9c-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="92f9c-158">Bir Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen, yönetici ayrıcalıklarıyla açılmış Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-158">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="92f9c-159">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="92f9c-159">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="92f9c-160">Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="92f9c-161">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="92f9c-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="92f9c-162">Service\bin. adresinden Service. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="92f9c-162">Launch Service.exe from service\bin.</span></span>

3. <span data-ttu-id="92f9c-163">\Client\bin. adresinden Client. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="92f9c-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="92f9c-164">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="92f9c-164">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="92f9c-165">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="92f9c-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="92f9c-166">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="92f9c-166">To run the sample across computers</span></span>

1. <span data-ttu-id="92f9c-167">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92f9c-167">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="92f9c-168">Hizmet programı dosyalarını \service\bin konumundan hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="92f9c-169">Ayrıca Setup. bat, Cleanup. bat, GetComputerName. vbs ve ImportClientCert. bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="92f9c-170">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92f9c-170">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="92f9c-171">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="92f9c-172">Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="92f9c-173">Sunucusunda, yönetici ayrıcalıklarıyla açılan `setup.bat service` bir Visual Studio için geliştirici komut istemi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92f9c-174">`service` Bağımsız değişkeniyle birlikte çalıştırmak `setup.bat` , bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>

6. <span data-ttu-id="92f9c-175">Service. exe. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni `findValue` sertifika adını ( [ \<ServiceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="92f9c-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="92f9c-176">Ayrıca, \<Service>/\<BaseAddresses> öğesindeki bilgisayar adını localhost 'dan tam olarak tam adı olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="92f9c-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="92f9c-177">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="92f9c-178">İstemcisinde, yönetici ayrıcalıklarıyla açılan `setup.bat client` bir Visual Studio için geliştirici komut istemi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-178">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92f9c-179">Bağımsız `setup.bat` değişkeniyle birlikte `client` çalıştırmak, Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>

9. <span data-ttu-id="92f9c-180">İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="92f9c-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="92f9c-181">Localhost 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>

10. <span data-ttu-id="92f9c-182">Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="92f9c-183">İstemcide, yönetici ayrıcalıklarıyla açılan bir Geliştirici Komut İstemi Visual Studio için ImportServiceCert. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-183">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92f9c-184">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>

12. <span data-ttu-id="92f9c-185">Sunucusunda, yönetici ayrıcalıklarıyla açılmış bir Visual Studio için Geliştirici Komut İstemi ImportClientCert. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-185">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92f9c-186">Bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>

13. <span data-ttu-id="92f9c-187">Sunucu bilgisayarda, komut istemi penceresinden Service. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-187">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="92f9c-188">İstemci bilgisayarda, bir komut istemi penceresinden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="92f9c-189">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="92f9c-189">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="92f9c-190">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="92f9c-190">To clean up after the sample</span></span>

1. <span data-ttu-id="92f9c-191">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92f9c-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="92f9c-192">Bu, sunucu ve istemci sertifikalarını sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="92f9c-192">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="92f9c-193">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="92f9c-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="92f9c-194">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="92f9c-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="92f9c-195">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin:. `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="92f9c-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
