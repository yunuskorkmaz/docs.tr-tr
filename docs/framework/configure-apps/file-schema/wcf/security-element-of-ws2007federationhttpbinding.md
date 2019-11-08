---
title: <ws2007FederationHttpBinding> <security> öğesi
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738727"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="380a6-102">\<ws2007FederationHttpBinding \<güvenlik > öğesi ></span><span class="sxs-lookup"><span data-stu-id="380a6-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="380a6-103">[\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) öğesinin güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="380a6-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="380a6-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="380a6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="380a6-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="380a6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="380a6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="380a6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="380a6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="380a6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="380a6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="380a6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="380a6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="380a6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="380a6-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="380a6-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="380a6-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="380a6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="380a6-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="380a6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="380a6-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="380a6-113">Attributes</span></span>  
  
|<span data-ttu-id="380a6-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="380a6-114">Attribute</span></span>|<span data-ttu-id="380a6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="380a6-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="380a6-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="380a6-116">Optional.</span></span> <span data-ttu-id="380a6-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="380a6-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="380a6-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="380a6-118">The default value is `Message`.</span></span> <span data-ttu-id="380a6-119">Bu öznitelik <xref:System.ServiceModel.WSFederationHttpSecurityMode>türündedir.</span><span class="sxs-lookup"><span data-stu-id="380a6-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="380a6-120">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="380a6-120">mode Attribute</span></span>  
  
|<span data-ttu-id="380a6-121">Değer</span><span class="sxs-lookup"><span data-stu-id="380a6-121">Value</span></span>|<span data-ttu-id="380a6-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="380a6-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="380a6-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="380a6-123">None</span></span>|<span data-ttu-id="380a6-124">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="380a6-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="380a6-125">İleti</span><span class="sxs-lookup"><span data-stu-id="380a6-125">Message</span></span>|<span data-ttu-id="380a6-126">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="380a6-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="380a6-127">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="380a6-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="380a6-128">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="380a6-128">The service must be configured with a certificate.</span></span> <span data-ttu-id="380a6-129">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="380a6-129">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="380a6-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="380a6-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="380a6-131">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="380a6-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="380a6-132">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="380a6-132">The service must be configured with a certificate.</span></span> <span data-ttu-id="380a6-133">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="380a6-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="380a6-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="380a6-134">Child Elements</span></span>  
  
|<span data-ttu-id="380a6-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="380a6-135">Element</span></span>|<span data-ttu-id="380a6-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="380a6-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="380a6-137">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="380a6-137">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="380a6-138">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="380a6-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="380a6-139">Bu öğe <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="380a6-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="380a6-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="380a6-140">Parent Elements</span></span>  
  
|<span data-ttu-id="380a6-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="380a6-141">Element</span></span>|<span data-ttu-id="380a6-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="380a6-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="380a6-143">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="380a6-143">\<binding></span></span>](bindings.md)|<span data-ttu-id="380a6-144">[\<wsDualHttpBinding >](wsdualhttpbinding.md)'in tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="380a6-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="380a6-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="380a6-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="380a6-146">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="380a6-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="380a6-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="380a6-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="380a6-148">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="380a6-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="380a6-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="380a6-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="380a6-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="380a6-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="380a6-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="380a6-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="380a6-152">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="380a6-152">\<binding></span></span>](bindings.md)
