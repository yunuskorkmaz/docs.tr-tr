---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 8432463ff62e4b5e54a491b574cc6a5285efe220
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397952"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="48bcd-101">\<IssuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="48bcd-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="48bcd-102">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
<span data-ttu-id="48bcd-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="48bcd-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="48bcd-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="48bcd-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="48bcd-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="48bcd-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="48bcd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="48bcd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="48bcd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="48bcd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="48bcd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="48bcd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="48bcd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuedTokenParameters >**</span><span class="sxs-lookup"><span data-stu-id="48bcd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48bcd-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48bcd-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="48bcd-111">Tür</span><span class="sxs-lookup"><span data-stu-id="48bcd-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48bcd-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="48bcd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="48bcd-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48bcd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48bcd-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="48bcd-114">Attributes</span></span>  
  
|<span data-ttu-id="48bcd-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="48bcd-115">Attribute</span></span>|<span data-ttu-id="48bcd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48bcd-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48bcd-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="48bcd-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="48bcd-118">Bağlama tarafından desteklenmesi gereken güvenlik belirtimleri sürümlerini (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) belirtir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="48bcd-119">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="48bcd-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="48bcd-120">Yani ıonmode</span><span class="sxs-lookup"><span data-stu-id="48bcd-120">inclusionMode</span></span>|<span data-ttu-id="48bcd-121">Belirteç ekleme gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="48bcd-122">Bu öznitelik türü <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="48bcd-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="48bcd-123">keySize</span><span class="sxs-lookup"><span data-stu-id="48bcd-123">keySize</span></span>|<span data-ttu-id="48bcd-124">Belirteç anahtar boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="48bcd-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="48bcd-125">Varsayılan değer 256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-125">The default value is 256.</span></span>|  
|<span data-ttu-id="48bcd-126">Anahtar</span><span class="sxs-lookup"><span data-stu-id="48bcd-126">keyType</span></span>|<span data-ttu-id="48bcd-127">Anahtar türünü belirten geçerli <xref:System.IdentityModel.Tokens.SecurityKeyType> bir değeri.</span><span class="sxs-lookup"><span data-stu-id="48bcd-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="48bcd-128">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="48bcd-129">Belirteç</span><span class="sxs-lookup"><span data-stu-id="48bcd-129">tokenType</span></span>|<span data-ttu-id="48bcd-130">Belirteç türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="48bcd-130">A string that specifies the token type.</span></span> <span data-ttu-id="48bcd-131">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="48bcd-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48bcd-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="48bcd-132">Child Elements</span></span>  
  
|<span data-ttu-id="48bcd-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="48bcd-133">Element</span></span>|<span data-ttu-id="48bcd-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48bcd-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48bcd-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="48bcd-135">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="48bcd-136">Ek istek parametrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="48bcd-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="48bcd-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="48bcd-137">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="48bcd-138">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="48bcd-139">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="48bcd-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="48bcd-140">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48bcd-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="48bcd-141">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="48bcd-142">\<veren ></span><span class="sxs-lookup"><span data-stu-id="48bcd-142">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="48bcd-143">Geçerli belirteci veren bitiş noktasını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="48bcd-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="48bcd-144">\<IssuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="48bcd-144">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="48bcd-145">Belirteç verenin meta verilerinin uç nokta adresini belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="48bcd-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48bcd-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="48bcd-146">Parent Elements</span></span>  
  
|<span data-ttu-id="48bcd-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="48bcd-147">Element</span></span>|<span data-ttu-id="48bcd-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48bcd-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48bcd-149">\<Securebir Bootstrap ></span><span class="sxs-lookup"><span data-stu-id="48bcd-149">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="48bcd-150">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="48bcd-151">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="48bcd-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="48bcd-152">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="48bcd-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48bcd-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48bcd-153">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="48bcd-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="48bcd-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="48bcd-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="48bcd-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="48bcd-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="48bcd-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="48bcd-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="48bcd-157">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="48bcd-158">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="48bcd-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="48bcd-159">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="48bcd-159">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="48bcd-160">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="48bcd-160">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="48bcd-161">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="48bcd-161">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="48bcd-162">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="48bcd-162">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="48bcd-163">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="48bcd-163">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
