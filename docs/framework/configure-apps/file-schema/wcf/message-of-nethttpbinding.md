---
title: <message> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 62b1793d18ddc8edc1f55b02137c4e0a9f7327d2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738967"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="ff406-102">\<message> / \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ff406-102">\<message> of \<netHttpBinding></span></span>
<span data-ttu-id="ff406-103">İleti düzeyi güvenliği için ayarları tanımlar [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ff406-103">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="ff406-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff406-104">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff406-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff406-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ff406-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="ff406-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff406-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ff406-107">Attributes</span></span>  
  
|<span data-ttu-id="ff406-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ff406-108">Attribute</span></span>|<span data-ttu-id="ff406-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff406-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff406-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ff406-110">algorithmSuite</span></span>|<span data-ttu-id="ff406-111">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ff406-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="ff406-112">Bu öznitelik, <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> algoritmaları ve anahtar boyutlarını belirten türüdür.</span><span class="sxs-lookup"><span data-stu-id="ff406-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="ff406-113">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ff406-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="ff406-114">Varsayılan değer: `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="ff406-114">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="ff406-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="ff406-115">clientCredentialType</span></span>|<span data-ttu-id="ff406-116">İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff406-116">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="ff406-117">Varsayılan değer: `UserName`.</span><span class="sxs-lookup"><span data-stu-id="ff406-117">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ff406-118">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="ff406-118">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ff406-119">Değer</span><span class="sxs-lookup"><span data-stu-id="ff406-119">Value</span></span>|<span data-ttu-id="ff406-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff406-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ff406-121">UserName</span><span class="sxs-lookup"><span data-stu-id="ff406-121">UserName</span></span>|<span data-ttu-id="ff406-122">-İstemcinin bir Kullanıcı adı kimlik bilgisiyle sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ff406-122">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="ff406-123">Bu kimlik bilgisinin <> öğesi kullanılarak belirtilmesi gerekir `clientCredentials` .</span><span class="sxs-lookup"><span data-stu-id="ff406-123">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="ff406-124">-WCF parola özetinin gönderilmesini veya parolaları kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ff406-124">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="ff406-125">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="ff406-125">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="ff406-126">İçin, `basicHttpBinding` bunun için BIR SSL kanalı ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff406-126">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="ff406-127">Sertifika</span><span class="sxs-lookup"><span data-stu-id="ff406-127">Certificate</span></span>|<span data-ttu-id="ff406-128">İstemcinin bir sertifika kullanarak sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ff406-128">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="ff406-129">Bu durumda istemci kimlik bilgisinin <`clientCredentials`> ve <> kullanılarak belirtilmesi gerekir `clientCertificate` .</span><span class="sxs-lookup"><span data-stu-id="ff406-129">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="ff406-130">Ayrıca, ileti güvenliği modunu kullanırken, istemcinin hizmet sertifikasıyla sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff406-130">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="ff406-131">Bu durumda hizmet kimlik bilgilerinin <xref:System.ServiceModel.Description.ClientCredentials> sınıf veya `ClientCredentials` davranış öğesi kullanılarak belirtilmesi ve serviceCredentials öğesi kullanılarak hizmet sertifikası belirtilmesi gerekir \<serviceCertificate> .</span><span class="sxs-lookup"><span data-stu-id="ff406-131">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff406-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff406-132">Child Elements</span></span>  
 <span data-ttu-id="ff406-133">Yok</span><span class="sxs-lookup"><span data-stu-id="ff406-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff406-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff406-134">Parent Elements</span></span>  
  
|<span data-ttu-id="ff406-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff406-135">Element</span></span>|<span data-ttu-id="ff406-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff406-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff406-137"><`security`<> öğesi`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="ff406-137"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="ff406-138"><> öğesi için güvenlik yeteneklerini tanımlar `netHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="ff406-138">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff406-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff406-139">Example</span></span>  
 <span data-ttu-id="ff406-140">Bu örnek, basicHttpBinding ve ileti güvenliği kullanan bir uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff406-140">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="ff406-141">Bir hizmet için aşağıdaki yapılandırma örneğinde, uç nokta tanımı basicHttpBinding öğesini belirtir ve adlı bir bağlama yapılandırmasına başvurur `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="ff406-141">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="ff406-142">Hizmetin istemcinin kimliğini doğrulamak için kullandığı sertifika, `behaviors` öğesinin altındaki yapılandırma dosyasının bölümünde ayarlanır `serviceCredentials` .</span><span class="sxs-lookup"><span data-stu-id="ff406-142">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="ff406-143">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifika için geçerli olan doğrulama modu, `behaviors` öğesinin altındaki bölümünde de ayarlanır `clientCertificate` .</span><span class="sxs-lookup"><span data-stu-id="ff406-143">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="ff406-144">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ff406-144">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff406-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff406-145">See also</span></span>

- [<span data-ttu-id="ff406-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ff406-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ff406-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ff406-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ff406-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ff406-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ff406-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ff406-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
