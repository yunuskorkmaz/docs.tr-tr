---
title: <security> / <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: ea029444cee331a235c7a2fc140b4321d7530063
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736321"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="b0cc3-102">\<wsFederationHttpBinding \<güvenlik > ></span><span class="sxs-lookup"><span data-stu-id="b0cc3-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="b0cc3-103">[\<wsFederationHttpBinding >](wsfederationhttpbinding.md)güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="b0cc3-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b0cc3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b0cc3-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b0cc3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b0cc3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b0cc3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b0cc3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b0cc3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="b0cc3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="b0cc3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b0cc3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="b0cc3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0cc3-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0cc3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0cc3-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0cc3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b0cc3-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0cc3-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0cc3-113">Attributes</span></span>  
  
|<span data-ttu-id="b0cc3-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0cc3-114">Attribute</span></span>|<span data-ttu-id="b0cc3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0cc3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0cc3-116">Mod</span><span class="sxs-lookup"><span data-stu-id="b0cc3-116">Mode</span></span>|<span data-ttu-id="b0cc3-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-117">Optional.</span></span> <span data-ttu-id="b0cc3-118">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b0cc3-119">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-119">The default value is `Message`.</span></span> <span data-ttu-id="b0cc3-120">Bu öznitelik <xref:System.ServiceModel.WSFederationHttpSecurityMode>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-120">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b0cc3-121">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="b0cc3-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="b0cc3-122">Değer</span><span class="sxs-lookup"><span data-stu-id="b0cc3-122">Value</span></span>|<span data-ttu-id="b0cc3-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0cc3-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0cc3-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-124">None</span></span>|<span data-ttu-id="b0cc3-125">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-125">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="b0cc3-126">İleti</span><span class="sxs-lookup"><span data-stu-id="b0cc3-126">Message</span></span>|<span data-ttu-id="b0cc3-127">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-127">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="b0cc3-128">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="b0cc3-129">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-129">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="b0cc3-130">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır</span><span class="sxs-lookup"><span data-stu-id="b0cc3-130">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="b0cc3-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="b0cc3-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="b0cc3-132">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-132">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="b0cc3-133">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-133">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="b0cc3-134">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-134">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0cc3-135">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0cc3-135">Child Elements</span></span>  
  
|<span data-ttu-id="b0cc3-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0cc3-136">Element</span></span>|<span data-ttu-id="b0cc3-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0cc3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0cc3-138">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="b0cc3-138">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="b0cc3-139">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-139">Defines the settings for the message-level security.</span></span> <span data-ttu-id="b0cc3-140">Bu öğe <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-140">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0cc3-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0cc3-141">Parent Elements</span></span>  
  
|<span data-ttu-id="b0cc3-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0cc3-142">Element</span></span>|<span data-ttu-id="b0cc3-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0cc3-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0cc3-144">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="b0cc3-144">\<binding></span></span>](bindings.md)|<span data-ttu-id="b0cc3-145">[\<wsDualHttpBinding >](wsdualhttpbinding.md)'in tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-145">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0cc3-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0cc3-146">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="b0cc3-147">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b0cc3-147">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="b0cc3-148">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b0cc3-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b0cc3-149">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="b0cc3-149">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b0cc3-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b0cc3-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b0cc3-151">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0cc3-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b0cc3-152">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b0cc3-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b0cc3-153">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="b0cc3-153">\<binding></span></span>](bindings.md)
