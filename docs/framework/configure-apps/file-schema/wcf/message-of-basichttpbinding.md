---
title: <message> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 748a734af8cf6767ce47cfffce9aec3ef627cb44
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736746"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="724ea-102">\<ileti > \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="724ea-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="724ea-103">[\<basicHttpBinding >](basichttpbinding.md)'in ileti düzeyinde güvenliğine yönelik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="724ea-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="724ea-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="724ea-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="724ea-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="724ea-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="724ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="724ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="724ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="724ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="724ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="724ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="724ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="724ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="724ea-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ileti >**</span><span class="sxs-lookup"><span data-stu-id="724ea-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724ea-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="724ea-111">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="724ea-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="724ea-112">Attributes and Elements</span></span>  
 <span data-ttu-id="724ea-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="724ea-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="724ea-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="724ea-114">Attributes</span></span>  
  
|<span data-ttu-id="724ea-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="724ea-115">Attribute</span></span>|<span data-ttu-id="724ea-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="724ea-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="724ea-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="724ea-117">algorithmSuite</span></span>|<span data-ttu-id="724ea-118">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="724ea-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="724ea-119">Bu öznitelik, algoritmaları ve anahtar boyutlarını belirten <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türüdür.</span><span class="sxs-lookup"><span data-stu-id="724ea-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="724ea-120">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="724ea-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="724ea-121">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="724ea-121">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="724ea-122">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="724ea-122">clientCredentialType</span></span>|<span data-ttu-id="724ea-123">İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="724ea-123">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="724ea-124">Varsayılan, `UserName` değeridir.</span><span class="sxs-lookup"><span data-stu-id="724ea-124">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="724ea-125">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="724ea-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="724ea-126">Değer</span><span class="sxs-lookup"><span data-stu-id="724ea-126">Value</span></span>|<span data-ttu-id="724ea-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="724ea-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="724ea-128">UserName</span><span class="sxs-lookup"><span data-stu-id="724ea-128">UserName</span></span>|<span data-ttu-id="724ea-129">-İstemcinin bir Kullanıcı adı kimlik bilgisiyle sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="724ea-129">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="724ea-130">Bu kimlik bilgisinin [\<clientCredentials >](clientcredentials.md)kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="724ea-130">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="724ea-131">-WCF parola özetinin gönderilmesini veya parolaları kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="724ea-131">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="724ea-132">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="724ea-132">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="724ea-133">`basicHttpBinding`için bu, bir SSL kanalının ayarlanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="724ea-133">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="724ea-134">Sertifika</span><span class="sxs-lookup"><span data-stu-id="724ea-134">Certificate</span></span>|<span data-ttu-id="724ea-135">İstemcinin bir sertifika kullanarak sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="724ea-135">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="724ea-136">Bu durumda istemci kimlik bilgisinin [\<clientCredentials >](clientcredentials.md) ve [\<ClientCertificate >](clientcertificate-of-servicecredentials.md)kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="724ea-136">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="724ea-137">Ayrıca, ileti güvenliği modunu kullanırken, istemcinin hizmet sertifikasıyla sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="724ea-137">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="724ea-138">Bu durumda hizmet kimlik bilgilerinin <xref:System.ServiceModel.Description.ClientCredentials> sınıfı veya `ClientCredentials` davranış öğesi kullanılarak belirtilmesi ve [\<serviceCertificate >](servicecertificate-of-servicecredentials.md)kullanılarak hizmet sertifikası belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="724ea-138">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="724ea-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="724ea-139">Child Elements</span></span>  
 <span data-ttu-id="724ea-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="724ea-140">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="724ea-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="724ea-141">Parent Elements</span></span>  
  
|<span data-ttu-id="724ea-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="724ea-142">Element</span></span>|<span data-ttu-id="724ea-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="724ea-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="724ea-144">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="724ea-144">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="724ea-145">[\<basicHttpBinding >](basichttpbinding.md)için güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="724ea-145">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="724ea-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="724ea-146">Example</span></span>  
 <span data-ttu-id="724ea-147">Bu örnek, basicHttpBinding ve ileti güvenliği kullanan bir uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="724ea-147">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="724ea-148">Bir hizmet için aşağıdaki yapılandırma örneğinde, uç nokta tanımı basicHttpBinding 'i belirtir ve `Binding1`adlı bir bağlama yapılandırmasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="724ea-148">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="724ea-149">Hizmetin istemcinin kimliğini doğrulamak için kullandığı sertifika, `serviceCredentials` öğesi altındaki yapılandırma dosyasının `behaviors` bölümünde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="724ea-149">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="724ea-150">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifika için geçerli olan doğrulama modu, `clientCertificate` öğesi altındaki `behaviors` bölümünde da ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="724ea-150">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="724ea-151">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="724ea-151">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service -->
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
      <binding name="Binding1">
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
  
## <a name="see-also"></a><span data-ttu-id="724ea-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="724ea-152">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="724ea-153">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="724ea-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="724ea-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="724ea-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="724ea-155">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="724ea-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="724ea-156">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="724ea-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="724ea-157">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="724ea-157">\<binding></span></span>](bindings.md)
