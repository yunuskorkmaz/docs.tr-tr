---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251962"
---
# <a name="issuernameregistry"></a><span data-ttu-id="8c2b1-101">\<ıssuernameregbakanlığı ></span><span class="sxs-lookup"><span data-stu-id="8c2b1-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="8c2b1-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
<span data-ttu-id="8c2b1-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c2b1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8c2b1-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="8c2b1-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="8c2b1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8c2b1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="8c2b1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="8c2b1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="8c2b1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8c2b1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="8c2b1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ıssuernameregbakanlığı >**</span><span class="sxs-lookup"><span data-stu-id="8c2b1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c2b1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c2b1-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c2b1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c2b1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c2b1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c2b1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8c2b1-112">Attributes</span></span>  
  
|<span data-ttu-id="8c2b1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8c2b1-113">Attribute</span></span>|<span data-ttu-id="8c2b1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c2b1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c2b1-115">türü</span><span class="sxs-lookup"><span data-stu-id="8c2b1-115">type</span></span>|<span data-ttu-id="8c2b1-116"><xref:System.IdentityModel.Tokens.IssuerNameRegistry> Sınıfından türeten bir tür.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="8c2b1-117">Özel `type`belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="8c2b1-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c2b1-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c2b1-118">Child Elements</span></span>  
  
|<span data-ttu-id="8c2b1-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="8c2b1-119">Element</span></span>|<span data-ttu-id="8c2b1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c2b1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c2b1-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="8c2b1-121">\<trustedIssuers></span></span>](trustedissuers.md)|<span data-ttu-id="8c2b1-122">Öznitelik, yapılandırma tabanlı veren adı kayıt defterini <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (sınıfı) belirttiğinde, [ \<trustedissuers >](trustedissuers.md) öğesinin belirtilmesi gerekir. `type`</span><span class="sxs-lookup"><span data-stu-id="8c2b1-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="8c2b1-123">`<add>` `<clear>` `<remove>` [ Trustedissuers>öğesi\<](trustedissuers.md) alt öğe olarak, veya öğelerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-123">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c2b1-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c2b1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8c2b1-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="8c2b1-125">Element</span></span>|<span data-ttu-id="8c2b1-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c2b1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c2b1-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8c2b1-127">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="8c2b1-128">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c2b1-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c2b1-129">Remarks</span></span>  
 <span data-ttu-id="8c2b1-130">Tüm verenin belirteçleri, bir veren adı kayıt defteri kullanılarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="8c2b1-131">Bu, <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfından türetilen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="8c2b1-132">Veren adı kayıt defteri, bir anımsatıcı adını, ilgili veren tarafından üretilen belirteçlerin imzalarını doğrulamak için gereken şifreleme malzemesiyle ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="8c2b1-133">Veren adı kayıt defteri, bağlı olan taraf (RP) uygulaması tarafından güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="8c2b1-134">Veren adı kayıt defterinin türü, `type` özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="8c2b1-135">`<issuerNameRegistry>` Öğe, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="8c2b1-136"><xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> Yöntemi geçersiz kılarak bu alt öğeleri işleyen mantığı sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="8c2b1-137">WIF, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfından tek bir veren adı kayıt defteri türü sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="8c2b1-138">Bu sınıf, yapılandırmada belirtilen bir güvenilen veren sertifikaları kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="8c2b1-139">Bu, altında güvenilir veren sertifikaları koleksiyonunun `<trustedIssuers>`yapılandırıldığı bir alt yapılandırma öğesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="8c2b1-140">Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve, `<add>` `<clear>`veya `<remove>` öğeleri kullanılarak koleksiyona eklenir veya kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="8c2b1-141">`<issuerNameRegistry>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c2b1-142">Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="8c2b1-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="8c2b1-143">Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="8c2b1-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c2b1-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c2b1-144">Example</span></span>  
 <span data-ttu-id="8c2b1-145">Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c2b1-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c2b1-146">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
