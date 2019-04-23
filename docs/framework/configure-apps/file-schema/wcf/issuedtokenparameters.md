---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 6bdf56e3d2084dec8d44e1c4d3f0c1e50b711b92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153146"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="37b79-101">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="37b79-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="37b79-102">Bir federe güvenlik senaryosundaki güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="37b79-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="37b79-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="37b79-103">\<system.serviceModel></span></span>  
<span data-ttu-id="37b79-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="37b79-104">\<bindings></span></span>  
<span data-ttu-id="37b79-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="37b79-105">\<customBinding></span></span>  
<span data-ttu-id="37b79-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="37b79-106">\<binding></span></span>  
<span data-ttu-id="37b79-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="37b79-107">\<security></span></span>  
<span data-ttu-id="37b79-108">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="37b79-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37b79-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37b79-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="37b79-110">Tür</span><span class="sxs-lookup"><span data-stu-id="37b79-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37b79-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37b79-111">Attributes and Elements</span></span>  
 <span data-ttu-id="37b79-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37b79-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37b79-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37b79-113">Attributes</span></span>  
  
|<span data-ttu-id="37b79-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37b79-114">Attribute</span></span>|<span data-ttu-id="37b79-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37b79-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37b79-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="37b79-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="37b79-117">Güvenlik belirtimleri sürümlerini belirtir (WS-Security, WS-Trust, WS-Secure Conversation ve WS-Security Policy) bağlama tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="37b79-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="37b79-118">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="37b79-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="37b79-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="37b79-119">inclusionMode</span></span>|<span data-ttu-id="37b79-120">Belirteç ekleme gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="37b79-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="37b79-121">Bu öznitelik türünde <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="37b79-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="37b79-122">KeySize</span><span class="sxs-lookup"><span data-stu-id="37b79-122">keySize</span></span>|<span data-ttu-id="37b79-123">Belirteç anahtar boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="37b79-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="37b79-124">Varsayılan değer 256'dır.</span><span class="sxs-lookup"><span data-stu-id="37b79-124">The default value is 256.</span></span>|  
|<span data-ttu-id="37b79-125">KeyType</span><span class="sxs-lookup"><span data-stu-id="37b79-125">keyType</span></span>|<span data-ttu-id="37b79-126">Geçerli değerini <xref:System.IdentityModel.Tokens.SecurityKeyType> anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="37b79-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="37b79-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="37b79-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="37b79-128">TokenType</span><span class="sxs-lookup"><span data-stu-id="37b79-128">tokenType</span></span>|<span data-ttu-id="37b79-129">Belirteç türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="37b79-129">A string that specifies the token type.</span></span> <span data-ttu-id="37b79-130">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="37b79-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37b79-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37b79-131">Child Elements</span></span>  
  
|<span data-ttu-id="37b79-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="37b79-132">Element</span></span>|<span data-ttu-id="37b79-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37b79-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37b79-134">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="37b79-134">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="37b79-135">Ek istek parametrelerini belirten yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="37b79-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="37b79-136">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="37b79-136">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="37b79-137">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="37b79-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="37b79-138">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="37b79-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="37b79-139">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="37b79-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="37b79-140">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="37b79-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="37b79-141">\<veren ></span><span class="sxs-lookup"><span data-stu-id="37b79-141">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="37b79-142">Geçerli belirtecini veren uç noktasını belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="37b79-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="37b79-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="37b79-143">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="37b79-144">Belirteç Verenin meta veri uç nokta adresini belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="37b79-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37b79-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37b79-145">Parent Elements</span></span>  
  
|<span data-ttu-id="37b79-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="37b79-146">Element</span></span>|<span data-ttu-id="37b79-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37b79-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37b79-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="37b79-148">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="37b79-149">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="37b79-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="37b79-150">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="37b79-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="37b79-151">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="37b79-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37b79-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37b79-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="37b79-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="37b79-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="37b79-154">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="37b79-154">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="37b79-155">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="37b79-155">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="37b79-156">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="37b79-156">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="37b79-157">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="37b79-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="37b79-158">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="37b79-158">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="37b79-159">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="37b79-159">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="37b79-160">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="37b79-160">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="37b79-161">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="37b79-161">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="37b79-162">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="37b79-162">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
