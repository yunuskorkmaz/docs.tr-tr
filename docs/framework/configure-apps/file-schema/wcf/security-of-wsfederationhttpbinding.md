---
title: <security> / <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 75e3910473a353c2ef110106c34b4e92c018b51c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670423"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="a49bc-102">\<Güvenlik >, \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a49bc-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="a49bc-103">Güvenlik ayarlarını tanımlar [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a49bc-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="a49bc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a49bc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a49bc-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a49bc-105">\<bindings></span></span>  
<span data-ttu-id="a49bc-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a49bc-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a49bc-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a49bc-107">\<binding></span></span>  
<span data-ttu-id="a49bc-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a49bc-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a49bc-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a49bc-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a49bc-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a49bc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a49bc-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a49bc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a49bc-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a49bc-112">Attributes</span></span>  
  
|<span data-ttu-id="a49bc-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a49bc-113">Attribute</span></span>|<span data-ttu-id="a49bc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a49bc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a49bc-115">Mod</span><span class="sxs-lookup"><span data-stu-id="a49bc-115">Mode</span></span>|<span data-ttu-id="a49bc-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a49bc-116">Optional.</span></span> <span data-ttu-id="a49bc-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a49bc-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a49bc-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a49bc-118">The default value is `Message`.</span></span> <span data-ttu-id="a49bc-119">Bu öznitelik türünde <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a49bc-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a49bc-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="a49bc-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="a49bc-121">Değer</span><span class="sxs-lookup"><span data-stu-id="a49bc-121">Value</span></span>|<span data-ttu-id="a49bc-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a49bc-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a49bc-123">None</span><span class="sxs-lookup"><span data-stu-id="a49bc-123">None</span></span>|<span data-ttu-id="a49bc-124">SOAP ileti aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="a49bc-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="a49bc-125">İleti</span><span class="sxs-lookup"><span data-stu-id="a49bc-125">Message</span></span>|<span data-ttu-id="a49bc-126">SOAP ileti güveliği kullanarak bütünlüğü, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a49bc-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="a49bc-127">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="a49bc-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="a49bc-128">Hizmeti bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a49bc-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="a49bc-129">İstemci kimlik doğrulaması güvenlik belirteci hizmeti tarafından istemciye verilen belirtecin dayanır</span><span class="sxs-lookup"><span data-stu-id="a49bc-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="a49bc-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a49bc-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="a49bc-131">Bütünlüğü, gizliliği ve sunucu kimlik doğrulaması HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a49bc-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="a49bc-132">Hizmeti bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a49bc-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="a49bc-133">İstemci kimlik doğrulaması yoluyla SOAP ileti güvenliği sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirtecin dayanır.</span><span class="sxs-lookup"><span data-stu-id="a49bc-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a49bc-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a49bc-134">Child Elements</span></span>  
  
|<span data-ttu-id="a49bc-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="a49bc-135">Element</span></span>|<span data-ttu-id="a49bc-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a49bc-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a49bc-137">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a49bc-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a49bc-138">İleti düzeyi güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a49bc-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="a49bc-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="a49bc-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a49bc-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a49bc-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a49bc-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="a49bc-141">Element</span></span>|<span data-ttu-id="a49bc-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a49bc-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a49bc-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a49bc-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a49bc-144">Tüm bağlama yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a49bc-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a49bc-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a49bc-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="a49bc-146">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="a49bc-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="a49bc-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a49bc-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a49bc-148">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="a49bc-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="a49bc-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a49bc-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a49bc-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a49bc-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a49bc-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a49bc-151">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a49bc-152">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a49bc-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
