---
title: '&lt;İssuermetadata&gt;'
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: d3770764e75b3bfd1345ac6a44761861595309d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627466"
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="4ed36-102">&lt;İssuermetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="4ed36-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="4ed36-103">Bir federe güvenlik senaryosundaki güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="4ed36-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4ed36-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4ed36-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="4ed36-105">\<bindings></span></span>  
<span data-ttu-id="4ed36-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4ed36-106">\<customBinding></span></span>  
<span data-ttu-id="4ed36-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4ed36-107">\<binding></span></span>  
<span data-ttu-id="4ed36-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4ed36-108">\<security></span></span>  
<span data-ttu-id="4ed36-109">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="4ed36-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed36-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ed36-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="4ed36-111">Tür</span><span class="sxs-lookup"><span data-stu-id="4ed36-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ed36-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ed36-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4ed36-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ed36-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ed36-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ed36-114">Attributes</span></span>  
  
|<span data-ttu-id="4ed36-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4ed36-115">Attribute</span></span>|<span data-ttu-id="4ed36-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ed36-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ed36-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="4ed36-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="4ed36-118">Güvenlik belirtimleri sürümlerini belirtir (WS-Security, WS-Trust, WS-Secure Conversation ve WS-Security Policy) bağlama tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="4ed36-119">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="4ed36-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="4ed36-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="4ed36-120">inclusionMode</span></span>|<span data-ttu-id="4ed36-121">Belirteç ekleme gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="4ed36-122">Bu öznitelik türünde <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="4ed36-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="4ed36-123">KeySize</span><span class="sxs-lookup"><span data-stu-id="4ed36-123">keySize</span></span>|<span data-ttu-id="4ed36-124">Belirteç anahtar boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4ed36-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="4ed36-125">Varsayılan değer 256'dır.</span><span class="sxs-lookup"><span data-stu-id="4ed36-125">The default value is 256.</span></span>|  
|<span data-ttu-id="4ed36-126">KeyType</span><span class="sxs-lookup"><span data-stu-id="4ed36-126">keyType</span></span>|<span data-ttu-id="4ed36-127">Geçerli değerini <xref:System.IdentityModel.Tokens.SecurityKeyType> anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="4ed36-128">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="4ed36-129">TokenType</span><span class="sxs-lookup"><span data-stu-id="4ed36-129">tokenType</span></span>|<span data-ttu-id="4ed36-130">Belirteç türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4ed36-130">A string that specifies the token type.</span></span> <span data-ttu-id="4ed36-131">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="4ed36-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ed36-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ed36-132">Child Elements</span></span>  
  
|<span data-ttu-id="4ed36-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ed36-133">Element</span></span>|<span data-ttu-id="4ed36-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ed36-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ed36-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="4ed36-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="4ed36-136">Ek istek parametrelerini belirten yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4ed36-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="4ed36-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="4ed36-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="4ed36-138">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="4ed36-139">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="4ed36-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="4ed36-140">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="4ed36-141">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="4ed36-142">\<veren ></span><span class="sxs-lookup"><span data-stu-id="4ed36-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="4ed36-143">Geçerli belirtecini veren uç noktasını belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="4ed36-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="4ed36-144">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="4ed36-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="4ed36-145">Belirteç Verenin meta veri uç nokta adresini belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="4ed36-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ed36-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ed36-146">Parent Elements</span></span>  
  
|<span data-ttu-id="4ed36-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ed36-147">Element</span></span>|<span data-ttu-id="4ed36-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ed36-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ed36-149">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="4ed36-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="4ed36-150">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="4ed36-151">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4ed36-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="4ed36-152">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ed36-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ed36-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ed36-153">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4ed36-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4ed36-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4ed36-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4ed36-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4ed36-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4ed36-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4ed36-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4ed36-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="4ed36-158">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ed36-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="4ed36-159">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4ed36-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="4ed36-160">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="4ed36-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4ed36-161">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4ed36-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4ed36-162">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="4ed36-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="4ed36-163">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="4ed36-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
