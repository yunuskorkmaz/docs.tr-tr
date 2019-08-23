---
title: <security> / <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 875ce7d548d59f32465da817e9e956217f346f60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936533"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="a3237-102">\<\<WSFederationHttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a3237-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="a3237-103">WSFederationHttpBinding > güvenlik ayarlarını [ \<](wsfederationhttpbinding.md)tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a3237-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="a3237-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a3237-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a3237-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a3237-105">\<bindings></span></span>  
<span data-ttu-id="a3237-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a3237-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a3237-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a3237-107">\<binding></span></span>  
<span data-ttu-id="a3237-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a3237-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3237-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3237-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3237-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3237-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a3237-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3237-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3237-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3237-112">Attributes</span></span>  
  
|<span data-ttu-id="a3237-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a3237-113">Attribute</span></span>|<span data-ttu-id="a3237-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3237-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3237-115">Mod</span><span class="sxs-lookup"><span data-stu-id="a3237-115">Mode</span></span>|<span data-ttu-id="a3237-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a3237-116">Optional.</span></span> <span data-ttu-id="a3237-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3237-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a3237-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a3237-118">The default value is `Message`.</span></span> <span data-ttu-id="a3237-119">Bu öznitelik türü <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a3237-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a3237-120">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="a3237-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="a3237-121">Değer</span><span class="sxs-lookup"><span data-stu-id="a3237-121">Value</span></span>|<span data-ttu-id="a3237-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3237-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a3237-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="a3237-123">None</span></span>|<span data-ttu-id="a3237-124">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="a3237-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="a3237-125">`Message`</span><span class="sxs-lookup"><span data-stu-id="a3237-125">Message</span></span>|<span data-ttu-id="a3237-126">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a3237-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="a3237-127">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="a3237-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="a3237-128">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3237-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="a3237-129">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır</span><span class="sxs-lookup"><span data-stu-id="a3237-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="a3237-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a3237-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="a3237-131">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a3237-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="a3237-132">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3237-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="a3237-133">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="a3237-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3237-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3237-134">Child Elements</span></span>  
  
|<span data-ttu-id="a3237-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3237-135">Element</span></span>|<span data-ttu-id="a3237-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3237-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3237-137">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="a3237-137">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a3237-138">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a3237-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="a3237-139">Bu öğe türündedir <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="a3237-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3237-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3237-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a3237-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3237-141">Element</span></span>|<span data-ttu-id="a3237-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3237-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3237-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a3237-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="a3237-144">WSDualHttpBinding > Tüm bağlama yeteneklerini [ \<](wsdualhttpbinding.md)tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a3237-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3237-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3237-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="a3237-146">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3237-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="a3237-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a3237-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a3237-148">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="a3237-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="a3237-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a3237-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a3237-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a3237-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a3237-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a3237-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a3237-152">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a3237-152">\<binding></span></span>](../../../misc/binding.md)
