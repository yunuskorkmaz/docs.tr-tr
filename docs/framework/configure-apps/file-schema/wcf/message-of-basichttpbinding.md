---
description: 'Hakkında daha fazla bilgi <message> edinin: <basicHttpBinding>'
title: <message> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 738d782aaac06366eec324b091cbda815a3ff98f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802157"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="264cf-103">\<message> / \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="264cf-103">\<message> of \<basicHttpBinding></span></span>

<span data-ttu-id="264cf-104">İleti düzeyi güvenliği için ayarları tanımlar [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="264cf-104">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="264cf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="264cf-105">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="264cf-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="264cf-106">Attributes and Elements</span></span>  

 <span data-ttu-id="264cf-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="264cf-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="264cf-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="264cf-108">Attributes</span></span>  
  
|<span data-ttu-id="264cf-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="264cf-109">Attribute</span></span>|<span data-ttu-id="264cf-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="264cf-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="264cf-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="264cf-111">algorithmSuite</span></span>|<span data-ttu-id="264cf-112">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="264cf-112">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="264cf-113">Bu öznitelik, <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> algoritmaları ve anahtar boyutlarını belirten türüdür.</span><span class="sxs-lookup"><span data-stu-id="264cf-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="264cf-114">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="264cf-114">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="264cf-115">`Basic256` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="264cf-115">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="264cf-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="264cf-116">clientCredentialType</span></span>|<span data-ttu-id="264cf-117">İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="264cf-117">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="264cf-118">Varsayılan değer: `UserName`.</span><span class="sxs-lookup"><span data-stu-id="264cf-118">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="264cf-119">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="264cf-119">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="264cf-120">Değer</span><span class="sxs-lookup"><span data-stu-id="264cf-120">Value</span></span>|<span data-ttu-id="264cf-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="264cf-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="264cf-122">UserName</span><span class="sxs-lookup"><span data-stu-id="264cf-122">UserName</span></span>|<span data-ttu-id="264cf-123">-İstemcinin bir Kullanıcı adı kimlik bilgisiyle sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="264cf-123">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="264cf-124">Bu kimlik bilgisinin kullanılarak belirtilmesi gerekir [\<clientCredentials>](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="264cf-124">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="264cf-125">-WCF parola özetinin gönderilmesini veya parolaları kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="264cf-125">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="264cf-126">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="264cf-126">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="264cf-127">İçin, `basicHttpBinding` bunun için BIR SSL kanalı ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="264cf-127">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="264cf-128">Sertifika</span><span class="sxs-lookup"><span data-stu-id="264cf-128">Certificate</span></span>|<span data-ttu-id="264cf-129">İstemcinin bir sertifika kullanarak sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="264cf-129">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="264cf-130">Bu durumda istemci kimlik bilgisinin ve kullanılarak belirtilmesi gerekir [\<clientCredentials>](clientcredentials.md) [\<clientCertificate>](clientcertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="264cf-130">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="264cf-131">Ayrıca, ileti güvenliği modunu kullanırken, istemcinin hizmet sertifikasıyla sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="264cf-131">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="264cf-132">Bu durumda hizmet kimlik bilgilerinin <xref:System.ServiceModel.Description.ClientCredentials> sınıf veya `ClientCredentials` davranış öğesi kullanılarak belirtilmesi ve kullanılarak hizmet sertifikası belirtilmesi gerekir [\<serviceCertificate>](servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="264cf-132">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="264cf-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="264cf-133">Child Elements</span></span>  

 <span data-ttu-id="264cf-134">Yok</span><span class="sxs-lookup"><span data-stu-id="264cf-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="264cf-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="264cf-135">Parent Elements</span></span>  
  
|<span data-ttu-id="264cf-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="264cf-136">Element</span></span>|<span data-ttu-id="264cf-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="264cf-137">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="264cf-138">İçin güvenlik yeteneklerini tanımlar [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="264cf-138">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="264cf-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="264cf-139">Example</span></span>  

 <span data-ttu-id="264cf-140">Bu örnek, basicHttpBinding ve ileti güvenliği kullanan bir uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="264cf-140">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="264cf-141">Bir hizmet için aşağıdaki yapılandırma örneğinde, uç nokta tanımı basicHttpBinding öğesini belirtir ve adlı bir bağlama yapılandırmasına başvurur `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="264cf-141">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="264cf-142">Hizmetin istemcinin kimliğini doğrulamak için kullandığı sertifika, `behaviors` öğesinin altındaki yapılandırma dosyasının bölümünde ayarlanır `serviceCredentials` .</span><span class="sxs-lookup"><span data-stu-id="264cf-142">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="264cf-143">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifika için geçerli olan doğrulama modu, `behaviors` öğesinin altındaki bölümünde de ayarlanır `clientCertificate` .</span><span class="sxs-lookup"><span data-stu-id="264cf-143">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="264cf-144">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="264cf-144">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="264cf-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="264cf-145">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="264cf-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="264cf-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="264cf-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="264cf-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="264cf-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="264cf-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="264cf-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="264cf-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
