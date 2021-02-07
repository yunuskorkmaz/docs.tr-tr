---
description: 'Hakkında daha fazla bilgi edinin: <issuedTokenParameters>'
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 92c8f5aa25ddb71561eb702ba3eb0396456008a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725668"
---
# \<issuedTokenParameters>

<span data-ttu-id="de094-102">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="de094-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="de094-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="de094-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="de094-104">Tür</span><span class="sxs-lookup"><span data-stu-id="de094-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de094-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de094-105">Attributes and Elements</span></span>  

 <span data-ttu-id="de094-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de094-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de094-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de094-107">Attributes</span></span>  
  
|<span data-ttu-id="de094-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de094-108">Attribute</span></span>|<span data-ttu-id="de094-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de094-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de094-110">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="de094-110">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="de094-111">Bağlama tarafından desteklenmesi gereken güvenlik belirtimleri sürümlerini (WS-Security, WS-Trust, WS-Secure Conversation ve WS-Security Policy) belirtir.</span><span class="sxs-lookup"><span data-stu-id="de094-111">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="de094-112">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="de094-112">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="de094-113">Yani ıonmode</span><span class="sxs-lookup"><span data-stu-id="de094-113">inclusionMode</span></span>|<span data-ttu-id="de094-114">Belirteç ekleme gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de094-114">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="de094-115">Bu öznitelik türü <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> .</span><span class="sxs-lookup"><span data-stu-id="de094-115">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="de094-116">keySize</span><span class="sxs-lookup"><span data-stu-id="de094-116">keySize</span></span>|<span data-ttu-id="de094-117">Belirteç anahtar boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="de094-117">An integer that specifies the token key size.</span></span> <span data-ttu-id="de094-118">Varsayılan değer 256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="de094-118">The default value is 256.</span></span>|  
|<span data-ttu-id="de094-119">Anahtar</span><span class="sxs-lookup"><span data-stu-id="de094-119">keyType</span></span>|<span data-ttu-id="de094-120"><xref:System.IdentityModel.Tokens.SecurityKeyType>Anahtar türünü belirten geçerli bir değeri.</span><span class="sxs-lookup"><span data-stu-id="de094-120">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="de094-121">Varsayılan değer: `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="de094-121">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="de094-122">Belirteç</span><span class="sxs-lookup"><span data-stu-id="de094-122">tokenType</span></span>|<span data-ttu-id="de094-123">Belirteç türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="de094-123">A string that specifies the token type.</span></span> <span data-ttu-id="de094-124">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="de094-124">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de094-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de094-125">Child Elements</span></span>  
  
|<span data-ttu-id="de094-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="de094-126">Element</span></span>|<span data-ttu-id="de094-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de094-127">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="de094-128">Ek istek parametrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="de094-128">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="de094-129">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="de094-129">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="de094-130">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="de094-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="de094-131">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de094-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="de094-132">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de094-132">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="de094-133">Geçerli belirteci veren bitiş noktasını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="de094-133">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="de094-134">Belirteç verenin meta verilerinin uç nokta adresini belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="de094-134">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de094-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de094-135">Parent Elements</span></span>  
  
|<span data-ttu-id="de094-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="de094-136">Element</span></span>|<span data-ttu-id="de094-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de094-137">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="de094-138">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="de094-138">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="de094-139">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de094-139">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de094-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de094-140">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="de094-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="de094-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="de094-142">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="de094-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="de094-143">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="de094-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="de094-144">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="de094-144">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="de094-145">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="de094-145">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="de094-146">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="de094-146">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="de094-147">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="de094-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="de094-148">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="de094-148">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="de094-149">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="de094-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
