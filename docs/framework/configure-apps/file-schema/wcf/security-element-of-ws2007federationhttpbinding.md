---
description: 'Hakkında daha fazla bilgi edinin: <security> öğesi <ws2007FederationHttpBinding>'
title: <security> öğesi <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 0caa2c3791c0dc3c8db0d9ee27175a28e52f6baa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683300"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="48dea-103">\<security> öğesi \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="48dea-103">\<security> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="48dea-104">Öğesinin güvenlik ayarlarını tanımlar [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="48dea-104">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="48dea-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="48dea-105">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48dea-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="48dea-106">Attributes and Elements</span></span>  

 <span data-ttu-id="48dea-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48dea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48dea-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="48dea-108">Attributes</span></span>  
  
|<span data-ttu-id="48dea-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="48dea-109">Attribute</span></span>|<span data-ttu-id="48dea-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48dea-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="48dea-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="48dea-111">Optional.</span></span> <span data-ttu-id="48dea-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="48dea-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="48dea-113">`Message` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="48dea-113">The default value is `Message`.</span></span> <span data-ttu-id="48dea-114">Bu öznitelik türü <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="48dea-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="48dea-115">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="48dea-115">mode Attribute</span></span>  
  
|<span data-ttu-id="48dea-116">Değer</span><span class="sxs-lookup"><span data-stu-id="48dea-116">Value</span></span>|<span data-ttu-id="48dea-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48dea-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48dea-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="48dea-118">None</span></span>|<span data-ttu-id="48dea-119">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="48dea-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="48dea-120">İleti</span><span class="sxs-lookup"><span data-stu-id="48dea-120">Message</span></span>|<span data-ttu-id="48dea-121">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="48dea-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="48dea-122">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="48dea-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="48dea-123">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48dea-123">The service must be configured with a certificate.</span></span> <span data-ttu-id="48dea-124">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="48dea-124">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="48dea-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="48dea-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="48dea-126">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="48dea-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="48dea-127">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48dea-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="48dea-128">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="48dea-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48dea-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="48dea-129">Child Elements</span></span>  
  
|<span data-ttu-id="48dea-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="48dea-130">Element</span></span>|<span data-ttu-id="48dea-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48dea-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="48dea-132">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48dea-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="48dea-133">Bu öğe türündedir <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="48dea-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48dea-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="48dea-134">Parent Elements</span></span>  
  
|<span data-ttu-id="48dea-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="48dea-135">Element</span></span>|<span data-ttu-id="48dea-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48dea-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="48dea-137">Öğesinin tüm bağlama yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="48dea-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48dea-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48dea-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="48dea-139">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="48dea-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="48dea-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="48dea-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="48dea-141">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="48dea-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="48dea-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="48dea-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="48dea-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48dea-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="48dea-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="48dea-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
