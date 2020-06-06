---
title: <security> / <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: ea029444cee331a235c7a2fc140b4321d7530063
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736321"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="39087-102">\<security> / \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="39087-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="39087-103">Öğesinin güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="39087-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="39087-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39087-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39087-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39087-105">Attributes and Elements</span></span>  
 <span data-ttu-id="39087-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39087-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39087-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39087-107">Attributes</span></span>  
  
|<span data-ttu-id="39087-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39087-108">Attribute</span></span>|<span data-ttu-id="39087-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39087-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39087-110">Mod</span><span class="sxs-lookup"><span data-stu-id="39087-110">Mode</span></span>|<span data-ttu-id="39087-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="39087-111">Optional.</span></span> <span data-ttu-id="39087-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="39087-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="39087-113">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="39087-113">The default value is `Message`.</span></span> <span data-ttu-id="39087-114">Bu öznitelik türü <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="39087-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="39087-115">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="39087-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="39087-116">Değer</span><span class="sxs-lookup"><span data-stu-id="39087-116">Value</span></span>|<span data-ttu-id="39087-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39087-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39087-118">Yok</span><span class="sxs-lookup"><span data-stu-id="39087-118">None</span></span>|<span data-ttu-id="39087-119">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="39087-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="39087-120">İleti</span><span class="sxs-lookup"><span data-stu-id="39087-120">Message</span></span>|<span data-ttu-id="39087-121">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="39087-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="39087-122">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="39087-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="39087-123">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="39087-123">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="39087-124">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır</span><span class="sxs-lookup"><span data-stu-id="39087-124">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="39087-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="39087-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="39087-126">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="39087-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="39087-127">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="39087-127">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="39087-128">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="39087-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39087-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39087-129">Child Elements</span></span>  
  
|<span data-ttu-id="39087-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="39087-130">Element</span></span>|<span data-ttu-id="39087-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39087-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="39087-132">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39087-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="39087-133">Bu öğe türündedir <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="39087-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39087-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39087-134">Parent Elements</span></span>  
  
|<span data-ttu-id="39087-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="39087-135">Element</span></span>|<span data-ttu-id="39087-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39087-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="39087-137">Öğesinin tüm bağlama yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="39087-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39087-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39087-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="39087-139">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="39087-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="39087-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="39087-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="39087-141">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="39087-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="39087-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="39087-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="39087-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="39087-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="39087-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="39087-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
