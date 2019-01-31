---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 6b40bd6edd27f4c3b4b530387417311e1f93a921
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283601"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="cc741-101">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="cc741-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="cc741-102">Bir federe güvenlik senaryosundaki güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc741-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="cc741-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cc741-103">\<system.serviceModel></span></span>  
<span data-ttu-id="cc741-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="cc741-104">\<bindings></span></span>  
<span data-ttu-id="cc741-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cc741-105">\<customBinding></span></span>  
<span data-ttu-id="cc741-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cc741-106">\<binding></span></span>  
<span data-ttu-id="cc741-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cc741-107">\<security></span></span>  
<span data-ttu-id="cc741-108">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="cc741-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc741-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc741-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="cc741-110">Tür</span><span class="sxs-lookup"><span data-stu-id="cc741-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc741-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc741-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cc741-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc741-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc741-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc741-113">Attributes</span></span>  
  
|<span data-ttu-id="cc741-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cc741-114">Attribute</span></span>|<span data-ttu-id="cc741-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc741-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc741-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="cc741-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="cc741-117">Güvenlik belirtimleri sürümlerini belirtir (WS-Security, WS-Trust, WS-Secure Conversation ve WS-Security Policy) bağlama tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc741-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="cc741-118">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="cc741-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="cc741-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="cc741-119">inclusionMode</span></span>|<span data-ttu-id="cc741-120">Belirteç ekleme gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc741-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="cc741-121">Bu öznitelik türünde <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="cc741-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="cc741-122">KeySize</span><span class="sxs-lookup"><span data-stu-id="cc741-122">keySize</span></span>|<span data-ttu-id="cc741-123">Belirteç anahtar boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cc741-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="cc741-124">Varsayılan değer 256'dır.</span><span class="sxs-lookup"><span data-stu-id="cc741-124">The default value is 256.</span></span>|  
|<span data-ttu-id="cc741-125">KeyType</span><span class="sxs-lookup"><span data-stu-id="cc741-125">keyType</span></span>|<span data-ttu-id="cc741-126">Geçerli değerini <xref:System.IdentityModel.Tokens.SecurityKeyType> anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc741-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="cc741-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cc741-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="cc741-128">TokenType</span><span class="sxs-lookup"><span data-stu-id="cc741-128">tokenType</span></span>|<span data-ttu-id="cc741-129">Belirteç türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="cc741-129">A string that specifies the token type.</span></span> <span data-ttu-id="cc741-130">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="cc741-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc741-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc741-131">Child Elements</span></span>  
  
|<span data-ttu-id="cc741-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc741-132">Element</span></span>|<span data-ttu-id="cc741-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc741-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc741-134">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="cc741-134">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="cc741-135">Ek istek parametrelerini belirten yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cc741-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="cc741-136">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="cc741-136">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="cc741-137">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc741-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="cc741-138">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="cc741-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="cc741-139">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc741-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="cc741-140">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc741-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="cc741-141">\<veren ></span><span class="sxs-lookup"><span data-stu-id="cc741-141">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="cc741-142">Geçerli belirtecini veren uç noktasını belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="cc741-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="cc741-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="cc741-143">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="cc741-144">Belirteç Verenin meta veri uç nokta adresini belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="cc741-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc741-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc741-145">Parent Elements</span></span>  
  
|<span data-ttu-id="cc741-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc741-146">Element</span></span>|<span data-ttu-id="cc741-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc741-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc741-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="cc741-148">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="cc741-149">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc741-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="cc741-150">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cc741-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="cc741-151">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc741-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc741-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc741-152">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cc741-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cc741-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="cc741-154">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="cc741-154">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cc741-155">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cc741-155">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="cc741-156">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cc741-156">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="cc741-157">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc741-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="cc741-158">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cc741-158">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="cc741-159">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="cc741-159">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="cc741-160">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="cc741-160">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="cc741-161">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="cc741-161">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="cc741-162">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="cc741-162">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
