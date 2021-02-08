---
description: 'Hakkında daha fazla bilgi <security> edinin: <wsFederationHttpBinding>'
title: <security> / <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 6c01c7a50b05f1723b3620407eb5e5761bae35cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786804"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="a9d38-103">\<security> / \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a9d38-103">\<security> of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="a9d38-104">Öğesinin güvenlik ayarlarını tanımlar [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a9d38-104">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="a9d38-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a9d38-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9d38-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9d38-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a9d38-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9d38-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9d38-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a9d38-108">Attributes</span></span>  
  
|<span data-ttu-id="a9d38-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a9d38-109">Attribute</span></span>|<span data-ttu-id="a9d38-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9d38-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9d38-111">Mod</span><span class="sxs-lookup"><span data-stu-id="a9d38-111">Mode</span></span>|<span data-ttu-id="a9d38-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a9d38-112">Optional.</span></span> <span data-ttu-id="a9d38-113">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9d38-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a9d38-114">`Message` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a9d38-114">The default value is `Message`.</span></span> <span data-ttu-id="a9d38-115">Bu öznitelik türü <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="a9d38-115">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a9d38-116">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="a9d38-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="a9d38-117">Değer</span><span class="sxs-lookup"><span data-stu-id="a9d38-117">Value</span></span>|<span data-ttu-id="a9d38-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9d38-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a9d38-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="a9d38-119">None</span></span>|<span data-ttu-id="a9d38-120">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="a9d38-120">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="a9d38-121">İleti</span><span class="sxs-lookup"><span data-stu-id="a9d38-121">Message</span></span>|<span data-ttu-id="a9d38-122">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a9d38-122">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="a9d38-123">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="a9d38-123">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="a9d38-124">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9d38-124">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="a9d38-125">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır</span><span class="sxs-lookup"><span data-stu-id="a9d38-125">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="a9d38-126">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a9d38-126">TransportWithMessageCredential</span></span>|<span data-ttu-id="a9d38-127">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a9d38-127">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="a9d38-128">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9d38-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="a9d38-129">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="a9d38-129">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9d38-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9d38-130">Child Elements</span></span>  
  
|<span data-ttu-id="a9d38-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9d38-131">Element</span></span>|<span data-ttu-id="a9d38-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9d38-132">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a9d38-133">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9d38-133">Defines the settings for the message-level security.</span></span> <span data-ttu-id="a9d38-134">Bu öğe türündedir <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="a9d38-134">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9d38-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9d38-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a9d38-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9d38-136">Element</span></span>|<span data-ttu-id="a9d38-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9d38-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a9d38-138">Öğesinin tüm bağlama yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a9d38-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9d38-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9d38-139">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="a9d38-140">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9d38-140">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="a9d38-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a9d38-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a9d38-142">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="a9d38-142">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="a9d38-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a9d38-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a9d38-144">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a9d38-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a9d38-145">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a9d38-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
