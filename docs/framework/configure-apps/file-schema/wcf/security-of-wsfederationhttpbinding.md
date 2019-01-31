---
title: <security> , <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 5316060d4122a443dd0223ce1ee9cdd39efac0b8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282067"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="81926-102">\<Güvenlik >, \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="81926-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="81926-103">Güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="81926-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="81926-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="81926-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="81926-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="81926-105">\<bindings></span></span>  
<span data-ttu-id="81926-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="81926-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="81926-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="81926-107">\<binding></span></span>  
<span data-ttu-id="81926-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="81926-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81926-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81926-109">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81926-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81926-110">Attributes and Elements</span></span>  
 <span data-ttu-id="81926-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81926-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81926-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81926-112">Attributes</span></span>  
  
|<span data-ttu-id="81926-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81926-113">Attribute</span></span>|<span data-ttu-id="81926-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81926-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81926-115">Mod</span><span class="sxs-lookup"><span data-stu-id="81926-115">Mode</span></span>|<span data-ttu-id="81926-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="81926-116">Optional.</span></span> <span data-ttu-id="81926-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="81926-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="81926-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="81926-118">The default value is `Message`.</span></span> <span data-ttu-id="81926-119">Bu öznitelik türünde <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="81926-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="81926-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="81926-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="81926-121">Değer</span><span class="sxs-lookup"><span data-stu-id="81926-121">Value</span></span>|<span data-ttu-id="81926-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81926-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81926-123">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="81926-123">None</span></span>|<span data-ttu-id="81926-124">SOAP ileti aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="81926-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="81926-125">İleti</span><span class="sxs-lookup"><span data-stu-id="81926-125">Message</span></span>|<span data-ttu-id="81926-126">SOAP ileti güveliği kullanarak bütünlüğü, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81926-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="81926-127">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="81926-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="81926-128">Hizmeti bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="81926-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="81926-129">İstemci kimlik doğrulaması güvenlik belirteci hizmeti tarafından istemciye verilen belirtecin dayanır</span><span class="sxs-lookup"><span data-stu-id="81926-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="81926-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="81926-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="81926-131">Bütünlüğü, gizliliği ve sunucu kimlik doğrulaması HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81926-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="81926-132">Hizmeti bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="81926-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="81926-133">İstemci kimlik doğrulaması yoluyla SOAP ileti güvenliği sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirtecin dayanır.</span><span class="sxs-lookup"><span data-stu-id="81926-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81926-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81926-134">Child Elements</span></span>  
  
|<span data-ttu-id="81926-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="81926-135">Element</span></span>|<span data-ttu-id="81926-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81926-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81926-137">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="81926-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="81926-138">İleti düzeyi güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81926-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="81926-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="81926-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81926-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81926-140">Parent Elements</span></span>  
  
|<span data-ttu-id="81926-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="81926-141">Element</span></span>|<span data-ttu-id="81926-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81926-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81926-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="81926-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="81926-144">Tüm bağlama yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="81926-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81926-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81926-145">See also</span></span>
- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="81926-146">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="81926-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="81926-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="81926-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="81926-148">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="81926-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="81926-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="81926-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="81926-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="81926-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81926-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="81926-151">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="81926-152">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="81926-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
