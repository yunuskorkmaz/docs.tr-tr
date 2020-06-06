---
title: <security>öğesi<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738727"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="e36e3-102">\<security>öğesi\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e36e3-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="e36e3-103">Öğesinin güvenlik ayarlarını tanımlar [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e36e3-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="e36e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e36e3-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e36e3-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e36e3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e36e3-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e36e3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e36e3-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e36e3-107">Attributes</span></span>  
  
|<span data-ttu-id="e36e3-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e36e3-108">Attribute</span></span>|<span data-ttu-id="e36e3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36e3-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="e36e3-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e36e3-110">Optional.</span></span> <span data-ttu-id="e36e3-111">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e36e3-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e36e3-112">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="e36e3-112">The default value is `Message`.</span></span> <span data-ttu-id="e36e3-113">Bu öznitelik türü <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="e36e3-113">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e36e3-114">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="e36e3-114">mode Attribute</span></span>  
  
|<span data-ttu-id="e36e3-115">Değer</span><span class="sxs-lookup"><span data-stu-id="e36e3-115">Value</span></span>|<span data-ttu-id="e36e3-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36e3-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e36e3-117">Yok</span><span class="sxs-lookup"><span data-stu-id="e36e3-117">None</span></span>|<span data-ttu-id="e36e3-118">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="e36e3-118">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="e36e3-119">İleti</span><span class="sxs-lookup"><span data-stu-id="e36e3-119">Message</span></span>|<span data-ttu-id="e36e3-120">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e36e3-120">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="e36e3-121">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="e36e3-121">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="e36e3-122">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e36e3-122">The service must be configured with a certificate.</span></span> <span data-ttu-id="e36e3-123">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="e36e3-123">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="e36e3-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e36e3-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="e36e3-125">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e36e3-125">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="e36e3-126">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e36e3-126">The service must be configured with a certificate.</span></span> <span data-ttu-id="e36e3-127">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="e36e3-127">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e36e3-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e36e3-128">Child Elements</span></span>  
  
|<span data-ttu-id="e36e3-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="e36e3-129">Element</span></span>|<span data-ttu-id="e36e3-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36e3-130">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="e36e3-131">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e36e3-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="e36e3-132">Bu öğe türündedir <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="e36e3-132">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e36e3-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e36e3-133">Parent Elements</span></span>  
  
|<span data-ttu-id="e36e3-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="e36e3-134">Element</span></span>|<span data-ttu-id="e36e3-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36e3-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e36e3-136">Öğesinin tüm bağlama yeteneklerini tanımlar [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e36e3-136">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e36e3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e36e3-137">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="e36e3-138">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e36e3-138">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="e36e3-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e36e3-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e36e3-140">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="e36e3-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="e36e3-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e36e3-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e36e3-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e36e3-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e36e3-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e36e3-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
