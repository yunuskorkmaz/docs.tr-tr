---
title: <message> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 62b1793d18ddc8edc1f55b02137c4e0a9f7327d2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738967"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="00035-102">\<netHttpBinding \<ileti > ></span><span class="sxs-lookup"><span data-stu-id="00035-102">\<message> of \<netHttpBinding></span></span>
<span data-ttu-id="00035-103">[\<netHttpBinding >](nethttpbinding.md)ileti düzeyinde güvenliğe yönelik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="00035-103">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
<span data-ttu-id="00035-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="00035-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="00035-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="00035-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="00035-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="00035-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="00035-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="00035-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="00035-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="00035-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="00035-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="00035-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="00035-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ileti >**</span><span class="sxs-lookup"><span data-stu-id="00035-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00035-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00035-111">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00035-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="00035-112">Attributes and Elements</span></span>  
 <span data-ttu-id="00035-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="00035-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00035-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="00035-114">Attributes</span></span>  
  
|<span data-ttu-id="00035-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="00035-115">Attribute</span></span>|<span data-ttu-id="00035-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00035-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00035-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="00035-117">algorithmSuite</span></span>|<span data-ttu-id="00035-118">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="00035-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="00035-119">Bu öznitelik, algoritmaları ve anahtar boyutlarını belirten <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türüdür.</span><span class="sxs-lookup"><span data-stu-id="00035-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="00035-120">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="00035-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="00035-121">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="00035-121">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="00035-122">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="00035-122">clientCredentialType</span></span>|<span data-ttu-id="00035-123">İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="00035-123">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="00035-124">Varsayılan, `UserName` değeridir.</span><span class="sxs-lookup"><span data-stu-id="00035-124">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="00035-125">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="00035-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="00035-126">Değer</span><span class="sxs-lookup"><span data-stu-id="00035-126">Value</span></span>|<span data-ttu-id="00035-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00035-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="00035-128">UserName</span><span class="sxs-lookup"><span data-stu-id="00035-128">UserName</span></span>|<span data-ttu-id="00035-129">-İstemcinin bir Kullanıcı adı kimlik bilgisiyle sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="00035-129">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="00035-130">Bu kimlik bilgisinin <`clientCredentials`> öğesi kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="00035-130">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="00035-131">-WCF parola özetinin gönderilmesini veya parolaları kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="00035-131">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="00035-132">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="00035-132">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="00035-133">`basicHttpBinding`için bu, bir SSL kanalının ayarlanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="00035-133">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="00035-134">Sertifika</span><span class="sxs-lookup"><span data-stu-id="00035-134">Certificate</span></span>|<span data-ttu-id="00035-135">İstemcinin bir sertifika kullanarak sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="00035-135">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="00035-136">Bu durumda istemci kimlik bilgisinin <`clientCredentials`> ve <`clientCertificate`> kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="00035-136">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="00035-137">Ayrıca, ileti güvenliği modunu kullanırken, istemcinin hizmet sertifikasıyla sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="00035-137">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="00035-138">Bu durumda hizmet kimlik bilgilerinin <xref:System.ServiceModel.Description.ClientCredentials> sınıfı veya `ClientCredentials` davranış öğesi kullanılarak belirtilmesi ve serviceCredentials öğesinin \<serviceCertificate > öğesi kullanılarak hizmet sertifikası belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="00035-138">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00035-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="00035-139">Child Elements</span></span>  
 <span data-ttu-id="00035-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="00035-140">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00035-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="00035-141">Parent Elements</span></span>  
  
|<span data-ttu-id="00035-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="00035-142">Element</span></span>|<span data-ttu-id="00035-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00035-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00035-144">`netHttpBinding`> `security`öğesi <></span><span class="sxs-lookup"><span data-stu-id="00035-144"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="00035-145"><`netHttpBinding`> öğesi için güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="00035-145">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00035-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="00035-146">Example</span></span>  
 <span data-ttu-id="00035-147">Bu örnek, basicHttpBinding ve ileti güvenliği kullanan bir uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="00035-147">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="00035-148">Bir hizmet için aşağıdaki yapılandırma örneğinde, uç nokta tanımı basicHttpBinding 'i belirtir ve `Binding1`adlı bir bağlama yapılandırmasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="00035-148">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="00035-149">Hizmetin istemcinin kimliğini doğrulamak için kullandığı sertifika, `serviceCredentials` öğesi altındaki yapılandırma dosyasının `behaviors` bölümünde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="00035-149">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="00035-150">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifika için geçerli olan doğrulama modu, `clientCertificate` öğesi altındaki `behaviors` bölümünde da ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="00035-150">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="00035-151">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00035-151">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
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
      <!-- This configuration defines the SecurityMode as Message and
           the clientCredentialType as Certificate. -->
      <binding name="Binding1" >
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
                 is in the user's Trusted People store, then it will be trusted without performing a
                 validation of the certificate's issuer chain. This setting is used here for convenience so that the
                 sample can be run without having to have certificates issued by a certification authority (CA).
                 This setting is less secure than the default, ChainTrust. The security implications of this
                 setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="00035-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00035-152">See also</span></span>

- [<span data-ttu-id="00035-153">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="00035-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="00035-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="00035-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="00035-155">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="00035-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="00035-156">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="00035-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="00035-157">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="00035-157">\<binding></span></span>](bindings.md)
