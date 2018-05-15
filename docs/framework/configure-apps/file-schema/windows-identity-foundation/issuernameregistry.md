---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b695cc6d66e5b9e45bb6a5fd22d594bc22ea3cba
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="5661c-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="5661c-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="5661c-103">Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan yayınlayıcı adı kaydını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5661c-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="5661c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5661c-104">\<system.identityModel></span></span>  
<span data-ttu-id="5661c-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5661c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5661c-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="5661c-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5661c-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5661c-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="5661c-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="5661c-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5661c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5661c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5661c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5661c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5661c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5661c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5661c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5661c-112">Attributes</span></span>  
  
|<span data-ttu-id="5661c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5661c-113">Attribute</span></span>|<span data-ttu-id="5661c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5661c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5661c-115">türü</span><span class="sxs-lookup"><span data-stu-id="5661c-115">type</span></span>|<span data-ttu-id="5661c-116">Türetilen bir tür <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5661c-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="5661c-117">Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvuruları] bakın.</span><span class="sxs-lookup"><span data-stu-id="5661c-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5661c-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5661c-118">Child Elements</span></span>  
  
|<span data-ttu-id="5661c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5661c-119">Element</span></span>|<span data-ttu-id="5661c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5661c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5661c-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="5661c-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="5661c-122">Zaman `type` özniteliği, yapılandırma tabanlı yayınlayıcı adı kaydını belirtir ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) öğesi belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5661c-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="5661c-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) öğesi alabilir `<add>`, `<clear>`, veya `<remove>` öğelerini alt öğe.</span><span class="sxs-lookup"><span data-stu-id="5661c-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5661c-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5661c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5661c-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="5661c-125">Element</span></span>|<span data-ttu-id="5661c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5661c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5661c-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5661c-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="5661c-128">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5661c-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5661c-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5661c-129">Remarks</span></span>  
 <span data-ttu-id="5661c-130">Tüm veren belirteçleri yayınlayıcı adı kaydını kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="5661c-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="5661c-131">Türetilen bir nesne budur <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5661c-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="5661c-132">Yayınlayıcı adı kaydını anımsatıcı adını karşılık gelen veren tarafından üretilen belirteçleri imzaları doğrulamak için gereken şifreleme malzeme ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5661c-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="5661c-133">Yayınlayıcı adı kaydını bağlı olan taraf (RP) uygulaması tarafından güvenilen verenlerin bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="5661c-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="5661c-134">Yayınlayıcı adı kaydını türünü kullanarak belirtilen `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5661c-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="5661c-135">`<issuerNameRegistry>` Öğesi, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5661c-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="5661c-136">Bu alt öğeleri geçersiz kılarak işler mantığın <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5661c-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="5661c-137">WIF sağlayan tek bir veren adı kayıt defteri türü kutusunda dışında <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5661c-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="5661c-138">Bu sınıf, yapılandırma dosyasında belirtilen güvenilen yayıncı sertifikaları kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5661c-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="5661c-139">Bir alt yapılandırma öğesi gerektiriyor `<trustedIssuers>`, güvenilen yayıncı sertifikaları koleksiyonunu yapılandırıldığı altında.</span><span class="sxs-lookup"><span data-stu-id="5661c-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="5661c-140">Sertifikaları ASN.1 kullanarak kodlanmış form sertifika parmak izi ve eklenir veya koleksiyondan kullanarak kaldırılır belirtilen güvenilen `<add>`, `<clear>`, veya `<remove>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="5661c-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="5661c-141">`<issuerNameRegistry>` Öğesi ile temsil edilir <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5661c-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5661c-142">Belirtme `<issuerNameRegistry>` öğesi bir alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak hala geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5661c-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="5661c-143">Ayarları `<securityTokenHandlerConfiguration>` öğesi geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5661c-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5661c-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="5661c-144">Example</span></span>  
 <span data-ttu-id="5661c-145">Aşağıdaki XML tabanlı yapılandırma veren belirtmek adı kayıt defteri gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5661c-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5661c-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5661c-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
