---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 07fc2c4c52c29de1cfc9f498a6dc6b6da887b502
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925340"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="ac874-101">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="ac874-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="ac874-102">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac874-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="ac874-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ac874-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ac874-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ac874-104">\<bindings></span></span>  
<span data-ttu-id="ac874-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ac874-105">\<customBinding></span></span>  
<span data-ttu-id="ac874-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ac874-106">\<binding></span></span>  
<span data-ttu-id="ac874-107">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ac874-107">\<security></span></span>  
<span data-ttu-id="ac874-108">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="ac874-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac874-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac874-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="ac874-110">Tür</span><span class="sxs-lookup"><span data-stu-id="ac874-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac874-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac874-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ac874-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac874-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac874-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ac874-113">Attributes</span></span>  
  
|<span data-ttu-id="ac874-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ac874-114">Attribute</span></span>|<span data-ttu-id="ac874-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac874-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac874-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="ac874-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="ac874-117">Bağlama tarafından desteklenmesi gereken güvenlik belirtimleri sürümlerini (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac874-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="ac874-118">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="ac874-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="ac874-119">Yani ıonmode</span><span class="sxs-lookup"><span data-stu-id="ac874-119">inclusionMode</span></span>|<span data-ttu-id="ac874-120">Belirteç ekleme gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac874-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="ac874-121">Bu öznitelik türü <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="ac874-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="ac874-122">keySize</span><span class="sxs-lookup"><span data-stu-id="ac874-122">keySize</span></span>|<span data-ttu-id="ac874-123">Belirteç anahtar boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ac874-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="ac874-124">Varsayılan değer 256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ac874-124">The default value is 256.</span></span>|  
|<span data-ttu-id="ac874-125">Anahtar</span><span class="sxs-lookup"><span data-stu-id="ac874-125">keyType</span></span>|<span data-ttu-id="ac874-126">Anahtar türünü belirten geçerli <xref:System.IdentityModel.Tokens.SecurityKeyType> bir değeri.</span><span class="sxs-lookup"><span data-stu-id="ac874-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="ac874-127">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="ac874-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="ac874-128">Belirteç</span><span class="sxs-lookup"><span data-stu-id="ac874-128">tokenType</span></span>|<span data-ttu-id="ac874-129">Belirteç türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ac874-129">A string that specifies the token type.</span></span> <span data-ttu-id="ac874-130">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="ac874-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac874-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac874-131">Child Elements</span></span>  
  
|<span data-ttu-id="ac874-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac874-132">Element</span></span>|<span data-ttu-id="ac874-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac874-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac874-134">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="ac874-134">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="ac874-135">Ek istek parametrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ac874-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="ac874-136">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="ac874-136">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="ac874-137">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac874-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="ac874-138">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="ac874-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="ac874-139">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac874-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="ac874-140">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac874-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="ac874-141">\<veren ></span><span class="sxs-lookup"><span data-stu-id="ac874-141">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="ac874-142">Geçerli belirteci veren bitiş noktasını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ac874-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="ac874-143">\<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="ac874-143">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="ac874-144">Belirteç verenin meta verilerinin uç nokta adresini belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ac874-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac874-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac874-145">Parent Elements</span></span>  
  
|<span data-ttu-id="ac874-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac874-146">Element</span></span>|<span data-ttu-id="ac874-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac874-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac874-148">\<Securebir Bootstrap ></span><span class="sxs-lookup"><span data-stu-id="ac874-148">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="ac874-149">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac874-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="ac874-150">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ac874-150">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="ac874-151">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac874-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac874-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac874-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ac874-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ac874-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ac874-154">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="ac874-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ac874-155">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ac874-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ac874-156">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ac874-156">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="ac874-157">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac874-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="ac874-158">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ac874-158">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="ac874-159">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="ac874-159">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ac874-160">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ac874-160">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ac874-161">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ac874-161">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ac874-162">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ac874-162">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
