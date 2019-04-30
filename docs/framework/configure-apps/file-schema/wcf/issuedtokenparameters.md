---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 6bdf56e3d2084dec8d44e1c4d3f0c1e50b711b92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758243"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="f0f3b-101">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="f0f3b-102">Bir federe güvenlik senaryosundaki güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="f0f3b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f0f3b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f0f3b-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-104">\<bindings></span></span>  
<span data-ttu-id="f0f3b-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-105">\<customBinding></span></span>  
<span data-ttu-id="f0f3b-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-106">\<binding></span></span>  
<span data-ttu-id="f0f3b-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-107">\<security></span></span>  
<span data-ttu-id="f0f3b-108">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f3b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0f3b-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="f0f3b-110">Tür</span><span class="sxs-lookup"><span data-stu-id="f0f3b-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0f3b-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0f3b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f0f3b-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0f3b-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0f3b-113">Attributes</span></span>  
  
|<span data-ttu-id="f0f3b-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f0f3b-114">Attribute</span></span>|<span data-ttu-id="f0f3b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0f3b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0f3b-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="f0f3b-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="f0f3b-117">Güvenlik belirtimleri sürümlerini belirtir (WS-Security, WS-Trust, WS-Secure Conversation ve WS-Security Policy) bağlama tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="f0f3b-118">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="f0f3b-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="f0f3b-119">inclusionMode</span></span>|<span data-ttu-id="f0f3b-120">Belirteç ekleme gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="f0f3b-121">Bu öznitelik türünde <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="f0f3b-122">KeySize</span><span class="sxs-lookup"><span data-stu-id="f0f3b-122">keySize</span></span>|<span data-ttu-id="f0f3b-123">Belirteç anahtar boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="f0f3b-124">Varsayılan değer 256'dır.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-124">The default value is 256.</span></span>|  
|<span data-ttu-id="f0f3b-125">KeyType</span><span class="sxs-lookup"><span data-stu-id="f0f3b-125">keyType</span></span>|<span data-ttu-id="f0f3b-126">Geçerli değerini <xref:System.IdentityModel.Tokens.SecurityKeyType> anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="f0f3b-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="f0f3b-128">TokenType</span><span class="sxs-lookup"><span data-stu-id="f0f3b-128">tokenType</span></span>|<span data-ttu-id="f0f3b-129">Belirteç türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-129">A string that specifies the token type.</span></span> <span data-ttu-id="f0f3b-130">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="f0f3b-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0f3b-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0f3b-131">Child Elements</span></span>  
  
|<span data-ttu-id="f0f3b-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0f3b-132">Element</span></span>|<span data-ttu-id="f0f3b-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0f3b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0f3b-134">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-134">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="f0f3b-135">Ek istek parametrelerini belirten yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="f0f3b-136">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-136">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="f0f3b-137">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="f0f3b-138">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="f0f3b-139">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="f0f3b-140">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="f0f3b-141">\<veren ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-141">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="f0f3b-142">Geçerli belirtecini veren uç noktasını belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="f0f3b-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="f0f3b-143">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="f0f3b-144">Belirteç Verenin meta veri uç nokta adresini belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0f3b-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0f3b-145">Parent Elements</span></span>  
  
|<span data-ttu-id="f0f3b-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0f3b-146">Element</span></span>|<span data-ttu-id="f0f3b-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0f3b-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0f3b-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="f0f3b-148">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="f0f3b-149">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="f0f3b-150">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="f0f3b-151">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0f3b-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0f3b-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f0f3b-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f0f3b-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f0f3b-154">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f0f3b-154">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f0f3b-155">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f0f3b-155">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f0f3b-156">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f0f3b-156">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="f0f3b-157">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0f3b-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="f0f3b-158">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f0f3b-158">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="f0f3b-159">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="f0f3b-159">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f0f3b-160">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="f0f3b-160">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f0f3b-161">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="f0f3b-161">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="f0f3b-162">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="f0f3b-162">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
