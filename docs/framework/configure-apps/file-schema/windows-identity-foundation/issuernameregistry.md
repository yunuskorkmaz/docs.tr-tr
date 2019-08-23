---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942674"
---
# <a name="issuernameregistry"></a><span data-ttu-id="36c23-101">\<ıssuernameregbakanlığı ></span><span class="sxs-lookup"><span data-stu-id="36c23-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="36c23-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="36c23-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="36c23-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="36c23-103">\<system.identityModel></span></span>  
<span data-ttu-id="36c23-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="36c23-104">\<identityConfiguration></span></span>  
<span data-ttu-id="36c23-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="36c23-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="36c23-106">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="36c23-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="36c23-107">\<ıssuernameregbakanlığı ></span><span class="sxs-lookup"><span data-stu-id="36c23-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c23-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36c23-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36c23-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36c23-109">Attributes and Elements</span></span>  
 <span data-ttu-id="36c23-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36c23-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36c23-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36c23-111">Attributes</span></span>  
  
|<span data-ttu-id="36c23-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="36c23-112">Attribute</span></span>|<span data-ttu-id="36c23-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36c23-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36c23-114">türü</span><span class="sxs-lookup"><span data-stu-id="36c23-114">type</span></span>|<span data-ttu-id="36c23-115"><xref:System.IdentityModel.Tokens.IssuerNameRegistry> Sınıfından türeten bir tür.</span><span class="sxs-lookup"><span data-stu-id="36c23-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="36c23-116">Özel `type`belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="36c23-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36c23-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36c23-117">Child Elements</span></span>  
  
|<span data-ttu-id="36c23-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="36c23-118">Element</span></span>|<span data-ttu-id="36c23-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36c23-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36c23-120">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="36c23-120">\<trustedIssuers></span></span>](trustedissuers.md)|<span data-ttu-id="36c23-121">Öznitelik, yapılandırma tabanlı veren adı kayıt defterini <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (sınıfı) belirttiğinde, [ \<trustedissuers >](trustedissuers.md) öğesinin belirtilmesi gerekir. `type`</span><span class="sxs-lookup"><span data-stu-id="36c23-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="36c23-122">`<add>` `<clear>` `<remove>` [ Trustedissuers>öğesi\<](trustedissuers.md) alt öğe olarak, veya öğelerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="36c23-122">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36c23-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36c23-123">Parent Elements</span></span>  
  
|<span data-ttu-id="36c23-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="36c23-124">Element</span></span>|<span data-ttu-id="36c23-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36c23-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36c23-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="36c23-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="36c23-127">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="36c23-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36c23-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36c23-128">Remarks</span></span>  
 <span data-ttu-id="36c23-129">Tüm verenin belirteçleri, bir veren adı kayıt defteri kullanılarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="36c23-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="36c23-130">Bu, <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfından türetilen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="36c23-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="36c23-131">Veren adı kayıt defteri, bir anımsatıcı adını, ilgili veren tarafından üretilen belirteçlerin imzalarını doğrulamak için gereken şifreleme malzemesiyle ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36c23-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="36c23-132">Veren adı kayıt defteri, bağlı olan taraf (RP) uygulaması tarafından güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="36c23-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="36c23-133">Veren adı kayıt defterinin türü, `type` özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="36c23-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="36c23-134">`<issuerNameRegistry>` Öğe, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="36c23-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="36c23-135"><xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> Yöntemi geçersiz kılarak bu alt öğeleri işleyen mantığı sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="36c23-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="36c23-136">WIF, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfından tek bir veren adı kayıt defteri türü sağlar.</span><span class="sxs-lookup"><span data-stu-id="36c23-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="36c23-137">Bu sınıf, yapılandırmada belirtilen bir güvenilen veren sertifikaları kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="36c23-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="36c23-138">Bu, altında güvenilir veren sertifikaları koleksiyonunun `<trustedIssuers>`yapılandırıldığı bir alt yapılandırma öğesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="36c23-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="36c23-139">Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve, `<add>` `<clear>`veya `<remove>` öğeleri kullanılarak koleksiyona eklenir veya kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="36c23-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="36c23-140">`<issuerNameRegistry>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="36c23-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36c23-141">Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="36c23-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="36c23-142">Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="36c23-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36c23-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="36c23-143">Example</span></span>  
 <span data-ttu-id="36c23-144">Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="36c23-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36c23-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36c23-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
