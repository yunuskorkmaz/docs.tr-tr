---
title: '&lt;basicHttpBinding&gt; &lt;iletisi&gt;'
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: f58fadbc3ac3f193232ad075c4973f6ac2f2d1f6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagegt-of-ltbasichttpbindinggt"></a><span data-ttu-id="1bf2c-102">&lt;basicHttpBinding&gt; &lt;iletisi&gt;</span><span class="sxs-lookup"><span data-stu-id="1bf2c-102">&lt;message&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="1bf2c-103">İleti düzeyi güvenliği ayarlarını tanımlar [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1bf2c-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="1bf2c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1bf2c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1bf2c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="1bf2c-105">\<bindings></span></span>  
<span data-ttu-id="1bf2c-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="1bf2c-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="1bf2c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1bf2c-107">\<binding></span></span>  
<span data-ttu-id="1bf2c-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="1bf2c-108">\<security></span></span>  
<span data-ttu-id="1bf2c-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="1bf2c-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf2c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bf2c-110">Syntax</span></span>  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bf2c-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bf2c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1bf2c-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="1bf2c-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bf2c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1bf2c-113">Attributes</span></span>  
  
|<span data-ttu-id="1bf2c-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1bf2c-114">Attribute</span></span>|<span data-ttu-id="1bf2c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bf2c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1bf2c-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="1bf2c-116">algorithmSuite</span></span>|<span data-ttu-id="1bf2c-117">İleti şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="1bf2c-118">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, algoritmalar ve anahtar boyutları belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="1bf2c-119">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="1bf2c-120">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="1bf2c-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="1bf2c-121">clientCredentialType</span></span>|<span data-ttu-id="1bf2c-122">İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="1bf2c-123">Varsayılan, `UserName` değeridir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="1bf2c-124">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="1bf2c-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1bf2c-125">Değer</span><span class="sxs-lookup"><span data-stu-id="1bf2c-125">Value</span></span>|<span data-ttu-id="1bf2c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bf2c-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1bf2c-127">UserName</span><span class="sxs-lookup"><span data-stu-id="1bf2c-127">UserName</span></span>|<span data-ttu-id="1bf2c-128">-İstemci kimlik doğrulaması bir kullanıcı adı kimlik bilgisi sunucuda gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="1bf2c-129">Bu kimlik bilgilerini kullanarak belirtilmesi gerekiyor [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="1bf2c-129">This credential needs to be specified using the [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span></span><br /><span data-ttu-id="1bf2c-130">-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir parola Özet gönderme veya parolaları kullanmanızı ve ileti güvenliği için bu anahtarları kullanarak anahtarları türetme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-130">-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="1bf2c-131">Bu nedenle, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] taşıma kullanıcı adı kimlik bilgileri kullanılırken korunması gerektiğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-131">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="1bf2c-132">İçin `basicHttpBinding`, bu SSL kanalı oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="1bf2c-133">Sertifika</span><span class="sxs-lookup"><span data-stu-id="1bf2c-133">Certificate</span></span>|<span data-ttu-id="1bf2c-134">Bir sertifika kullanarak sunucuya istemcinin kimliğinin doğrulanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="1bf2c-135">İstemci kimlik bilgileri bu durumda kullanarak belirtilmesi gerekiyor [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) ve [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="1bf2c-135">The client credential in this case needs to be specified using [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) and the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="1bf2c-136">Ayrıca, ileti güvenlik modunu kullanırken, istemci ile hizmet sertifikası hazırlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="1bf2c-137">Hizmet kimlik bilgilerini bu durumda kullanarak belirtilmesi gerekiyor <xref:System.ServiceModel.Description.ClientCredentials> sınıfı veya `ClientCredentials` davranışı öğesi ve hizmet belirterek sertifika kullanarak [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="1bf2c-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bf2c-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bf2c-138">Child Elements</span></span>  
 <span data-ttu-id="1bf2c-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1bf2c-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bf2c-140">Parent Elements</span></span>  
  
|<span data-ttu-id="1bf2c-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="1bf2c-141">Element</span></span>|<span data-ttu-id="1bf2c-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bf2c-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bf2c-143">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="1bf2c-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="1bf2c-144">Güvenlik özellikleri için tanımlar [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1bf2c-144">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1bf2c-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bf2c-145">Example</span></span>  
 <span data-ttu-id="1bf2c-146">Bu örnek, basicHttpBinding ve ileti güvenliği kullanan bir uygulamayı uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="1bf2c-147">Aşağıdaki yapılandırma örneği bir hizmet için uç nokta tanımı basicHttpBinding belirtir ve adlı bir bağlama yapılandırması başvuran `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="1bf2c-148">Hizmetin kendisi için istemci kimlik doğrulaması için kullandığı sertifika kümesinde `behaviors` altında yapılandırma dosyasının `serviceCredentials` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="1bf2c-149">İstemci hizmete kendi kimliğini doğrulamak için kullandığı sertifikayı uygulandığı doğrulama modu da kümesinde `behaviors` altında bölümünde `clientCertificate` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="1bf2c-150">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <basicHttpBinding>  
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
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
  
## <a name="see-also"></a><span data-ttu-id="1bf2c-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf2c-151">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpMessageSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>  
 [<span data-ttu-id="1bf2c-152">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1bf2c-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1bf2c-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1bf2c-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1bf2c-154">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1bf2c-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1bf2c-155">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="1bf2c-155">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="1bf2c-156">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1bf2c-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
