---
description: 'Hakkında daha fazla bilgi <message> edinin: <netHttpBinding>'
title: <message> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 508e58e58dbb298081a075588ddda87289c1a3d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749629"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="730b3-103">\<message> / \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="730b3-103">\<message> of \<netHttpBinding></span></span>

<span data-ttu-id="730b3-104">İleti düzeyi güvenliği için ayarları tanımlar [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="730b3-104">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="730b3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="730b3-105">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="730b3-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="730b3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="730b3-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="730b3-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="730b3-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="730b3-108">Attributes</span></span>  
  
|<span data-ttu-id="730b3-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="730b3-109">Attribute</span></span>|<span data-ttu-id="730b3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730b3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="730b3-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="730b3-111">algorithmSuite</span></span>|<span data-ttu-id="730b3-112">İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="730b3-112">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="730b3-113">Bu öznitelik, <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> algoritmaları ve anahtar boyutlarını belirten türüdür.</span><span class="sxs-lookup"><span data-stu-id="730b3-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="730b3-114">Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="730b3-114">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="730b3-115">`Basic256` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="730b3-115">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="730b3-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="730b3-116">clientCredentialType</span></span>|<span data-ttu-id="730b3-117">İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="730b3-117">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="730b3-118">Varsayılan değer: `UserName`.</span><span class="sxs-lookup"><span data-stu-id="730b3-118">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="730b3-119">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="730b3-119">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="730b3-120">Değer</span><span class="sxs-lookup"><span data-stu-id="730b3-120">Value</span></span>|<span data-ttu-id="730b3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730b3-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="730b3-122">UserName</span><span class="sxs-lookup"><span data-stu-id="730b3-122">UserName</span></span>|<span data-ttu-id="730b3-123">-İstemcinin bir Kullanıcı adı kimlik bilgisiyle sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="730b3-123">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="730b3-124">Bu kimlik bilgisinin <> öğesi kullanılarak belirtilmesi gerekir `clientCredentials` .</span><span class="sxs-lookup"><span data-stu-id="730b3-124">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="730b3-125">-WCF parola özetinin gönderilmesini veya parolaları kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="730b3-125">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="730b3-126">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="730b3-126">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="730b3-127">İçin, `basicHttpBinding` bunun için BIR SSL kanalı ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="730b3-127">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="730b3-128">Sertifika</span><span class="sxs-lookup"><span data-stu-id="730b3-128">Certificate</span></span>|<span data-ttu-id="730b3-129">İstemcinin bir sertifika kullanarak sunucuda kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="730b3-129">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="730b3-130">Bu durumda istemci kimlik bilgisinin <`clientCredentials`> ve <> kullanılarak belirtilmesi gerekir `clientCertificate` .</span><span class="sxs-lookup"><span data-stu-id="730b3-130">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="730b3-131">Ayrıca, ileti güvenliği modunu kullanırken, istemcinin hizmet sertifikasıyla sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="730b3-131">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="730b3-132">Bu durumda hizmet kimlik bilgilerinin <xref:System.ServiceModel.Description.ClientCredentials> sınıf veya `ClientCredentials` davranış öğesi kullanılarak belirtilmesi ve serviceCredentials öğesi kullanılarak hizmet sertifikası belirtilmesi gerekir \<serviceCertificate> .</span><span class="sxs-lookup"><span data-stu-id="730b3-132">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="730b3-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="730b3-133">Child Elements</span></span>  

 <span data-ttu-id="730b3-134">Yok</span><span class="sxs-lookup"><span data-stu-id="730b3-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="730b3-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="730b3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="730b3-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="730b3-136">Element</span></span>|<span data-ttu-id="730b3-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730b3-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="730b3-138"><`security` <> öğesi `netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="730b3-138"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="730b3-139"><> öğesi için güvenlik yeteneklerini tanımlar `netHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="730b3-139">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="730b3-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="730b3-140">Example</span></span>  

 <span data-ttu-id="730b3-141">Bu örnek, basicHttpBinding ve ileti güvenliği kullanan bir uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="730b3-141">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="730b3-142">Bir hizmet için aşağıdaki yapılandırma örneğinde, uç nokta tanımı basicHttpBinding öğesini belirtir ve adlı bir bağlama yapılandırmasına başvurur `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="730b3-142">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="730b3-143">Hizmetin istemcinin kimliğini doğrulamak için kullandığı sertifika, `behaviors` öğesinin altındaki yapılandırma dosyasının bölümünde ayarlanır `serviceCredentials` .</span><span class="sxs-lookup"><span data-stu-id="730b3-143">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="730b3-144">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifika için geçerli olan doğrulama modu, `behaviors` öğesinin altındaki bölümünde de ayarlanır `clientCertificate` .</span><span class="sxs-lookup"><span data-stu-id="730b3-144">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="730b3-145">Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="730b3-145">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="730b3-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="730b3-146">See also</span></span>

- [<span data-ttu-id="730b3-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="730b3-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="730b3-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="730b3-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="730b3-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="730b3-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="730b3-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="730b3-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
