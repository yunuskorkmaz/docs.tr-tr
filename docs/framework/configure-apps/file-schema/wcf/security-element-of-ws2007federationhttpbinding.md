---
title: <security>öğesi<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 61b56ca1fae5c328cda0bbebef4026f0784095a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936816"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="ed3d4-102">\<\<WS2007FederationHttpBinding > Güvenlik > öğesi</span><span class="sxs-lookup"><span data-stu-id="ed3d4-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="ed3d4-103">WS2007FederationHttpBinding > öğesinin güvenlik ayarlarını [ \<](ws2007federationhttpbinding.md) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="ed3d4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ed3d4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ed3d4-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ed3d4-105">\<bindings></span></span>  
<span data-ttu-id="ed3d4-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ed3d4-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="ed3d4-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ed3d4-107">\<binding></span></span>  
<span data-ttu-id="ed3d4-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ed3d4-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed3d4-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed3d4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed3d4-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed3d4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ed3d4-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed3d4-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed3d4-112">Attributes</span></span>  
  
|<span data-ttu-id="ed3d4-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ed3d4-113">Attribute</span></span>|<span data-ttu-id="ed3d4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3d4-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="ed3d4-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-115">Optional.</span></span> <span data-ttu-id="ed3d4-116">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="ed3d4-117">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-117">The default value is `Message`.</span></span> <span data-ttu-id="ed3d4-118">Bu öznitelik türü <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ed3d4-119">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="ed3d4-119">mode Attribute</span></span>  
  
|<span data-ttu-id="ed3d4-120">Değer</span><span class="sxs-lookup"><span data-stu-id="ed3d4-120">Value</span></span>|<span data-ttu-id="ed3d4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3d4-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed3d4-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-122">None</span></span>|<span data-ttu-id="ed3d4-123">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="ed3d4-124">`Message`</span><span class="sxs-lookup"><span data-stu-id="ed3d4-124">Message</span></span>|<span data-ttu-id="ed3d4-125">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="ed3d4-126">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="ed3d4-127">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="ed3d4-128">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="ed3d4-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="ed3d4-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="ed3d4-130">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="ed3d4-131">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="ed3d4-132">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed3d4-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed3d4-133">Child Elements</span></span>  
  
|<span data-ttu-id="ed3d4-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed3d4-134">Element</span></span>|<span data-ttu-id="ed3d4-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3d4-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed3d4-136">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="ed3d4-136">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="ed3d4-137">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="ed3d4-138">Bu öğe türündedir <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed3d4-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed3d4-139">Parent Elements</span></span>  
  
|<span data-ttu-id="ed3d4-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed3d4-140">Element</span></span>|<span data-ttu-id="ed3d4-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3d4-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed3d4-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ed3d4-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="ed3d4-143">WSDualHttpBinding > Tüm bağlama yeteneklerini [ \<](wsdualhttpbinding.md)tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed3d4-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed3d4-144">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="ed3d4-145">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed3d4-145">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="ed3d4-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ed3d4-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ed3d4-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="ed3d4-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ed3d4-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ed3d4-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ed3d4-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed3d4-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ed3d4-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ed3d4-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ed3d4-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ed3d4-151">\<binding></span></span>](../../../misc/binding.md)
