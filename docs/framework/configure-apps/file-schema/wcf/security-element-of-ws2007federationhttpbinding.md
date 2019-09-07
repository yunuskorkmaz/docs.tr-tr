---
title: <security>öğesi<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 450b2403b8cd4ec43a41fd27bccb3b77202820bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399899"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="36f2d-102">\<\<WS2007FederationHttpBinding > Güvenlik > öğesi</span><span class="sxs-lookup"><span data-stu-id="36f2d-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="36f2d-103">WS2007FederationHttpBinding > öğesinin güvenlik ayarlarını [ \<](ws2007federationhttpbinding.md) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36f2d-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="36f2d-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="36f2d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="36f2d-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="36f2d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="36f2d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="36f2d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="36f2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="36f2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="36f2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="36f2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="36f2d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="36f2d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f2d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36f2d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36f2d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36f2d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="36f2d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36f2d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36f2d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36f2d-113">Attributes</span></span>  
  
|<span data-ttu-id="36f2d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="36f2d-114">Attribute</span></span>|<span data-ttu-id="36f2d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36f2d-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="36f2d-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="36f2d-116">Optional.</span></span> <span data-ttu-id="36f2d-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="36f2d-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="36f2d-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="36f2d-118">The default value is `Message`.</span></span> <span data-ttu-id="36f2d-119">Bu öznitelik türü <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="36f2d-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="36f2d-120">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="36f2d-120">mode Attribute</span></span>  
  
|<span data-ttu-id="36f2d-121">Değer</span><span class="sxs-lookup"><span data-stu-id="36f2d-121">Value</span></span>|<span data-ttu-id="36f2d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36f2d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36f2d-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="36f2d-123">None</span></span>|<span data-ttu-id="36f2d-124">Aktarım sırasında SOAP iletisi güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="36f2d-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="36f2d-125">`Message`</span><span class="sxs-lookup"><span data-stu-id="36f2d-125">Message</span></span>|<span data-ttu-id="36f2d-126">Bütünlük, gizlilik, sunucu kimlik doğrulaması ve istemci kimlik doğrulaması, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="36f2d-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="36f2d-127">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="36f2d-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="36f2d-128">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36f2d-128">The service must be configured with a certificate.</span></span> <span data-ttu-id="36f2d-129">İstemci kimlik doğrulaması, bir güvenlik belirteci hizmeti tarafından istemciye verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="36f2d-129">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="36f2d-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="36f2d-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="36f2d-131">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, HTTPS tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="36f2d-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="36f2d-132">Hizmetin bir sertifikayla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36f2d-132">The service must be configured with a certificate.</span></span> <span data-ttu-id="36f2d-133">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır ve istemciye bir güvenlik belirteci hizmeti tarafından verilen belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="36f2d-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36f2d-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36f2d-134">Child Elements</span></span>  
  
|<span data-ttu-id="36f2d-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="36f2d-135">Element</span></span>|<span data-ttu-id="36f2d-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36f2d-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36f2d-137">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="36f2d-137">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="36f2d-138">İleti düzeyinde güvenlik için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36f2d-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="36f2d-139">Bu öğe türündedir <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="36f2d-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36f2d-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36f2d-140">Parent Elements</span></span>  
  
|<span data-ttu-id="36f2d-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="36f2d-141">Element</span></span>|<span data-ttu-id="36f2d-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36f2d-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36f2d-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="36f2d-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="36f2d-144">WSDualHttpBinding > Tüm bağlama yeteneklerini [ \<](wsdualhttpbinding.md)tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36f2d-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36f2d-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36f2d-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="36f2d-146">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="36f2d-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="36f2d-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="36f2d-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="36f2d-148">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="36f2d-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="36f2d-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="36f2d-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="36f2d-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36f2d-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="36f2d-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="36f2d-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="36f2d-152">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="36f2d-152">\<binding></span></span>](../../../misc/binding.md)
