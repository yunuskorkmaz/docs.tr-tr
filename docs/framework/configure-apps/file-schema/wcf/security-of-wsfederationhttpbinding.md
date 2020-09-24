---
title: <security> / <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 650483099c7d70450cfc56a9a28efac076d64675
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162249"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="8fc31-102">\<security> / \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8fc31-102">\<security> of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="8fc31-103">Öğesinin güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8fc31-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="8fc31-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8fc31-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fc31-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fc31-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8fc31-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8fc31-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fc31-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8fc31-107">Attributes</span></span>  
  
|<span data-ttu-id="8fc31-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8fc31-108">Attribute</span></span>|<span data-ttu-id="8fc31-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fc31-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8fc31-110">Mod</span><span class="sxs-lookup"><span data-stu-id="8fc31-110">Mode</span></span>|<span data-ttu-id="8fc31-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8fc31-111">Optional.</span></span> <span data-ttu-id="8fc31-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8fc31-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="8fc31-113">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="8fc31-113">The default value is `Message`.</span></span> <span data-ttu-id="8fc31-114">Bu öznitelik türü <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="8fc31-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8fc31-115">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="8fc31-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="8fc31-116">Değer</span><span class="sxs-lookup"><span data-stu-id="8fc31-116">Value</span></span>|<span data-ttu-id="8fc31-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fc31-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8fc31-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="8fc31-118">None</span></span>|<span data-ttu-id="8fc31-119">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="8fc31-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="8fc31-120">İleti</span><span class="sxs-lookup"><span data-stu-id="8fc31-120">Message</span></span>|<span data-ttu-id="8fc31-121">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8fc31-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="8fc31-122">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="8fc31-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="8fc31-123">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fc31-123">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="8fc31-124">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır</span><span class="sxs-lookup"><span data-stu-id="8fc31-124">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="8fc31-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8fc31-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="8fc31-126">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8fc31-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="8fc31-127">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fc31-127">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="8fc31-128">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="8fc31-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fc31-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fc31-129">Child Elements</span></span>  
  
|<span data-ttu-id="8fc31-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fc31-130">Element</span></span>|<span data-ttu-id="8fc31-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fc31-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="8fc31-132">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8fc31-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="8fc31-133">Bu öğe türündedir <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="8fc31-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fc31-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fc31-134">Parent Elements</span></span>  
  
|<span data-ttu-id="8fc31-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fc31-135">Element</span></span>|<span data-ttu-id="8fc31-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fc31-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8fc31-137">Öğesinin tüm bağlama yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8fc31-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fc31-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fc31-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="8fc31-139">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fc31-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="8fc31-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8fc31-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8fc31-141">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="8fc31-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="8fc31-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8fc31-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8fc31-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8fc31-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8fc31-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8fc31-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
