---
title: '&lt;issuerTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 02e2beb285cb0c4d88f98c3155ab5a3ff5e31e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="b580d-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="b580d-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="b580d-103">Belirteci işleyicisi koleksiyonundaki işleyiciler tarafından kullanılan veren belirteci çözümleyiciyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b580d-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="b580d-104">Veren belirteç Çözümleyicisi gelen iletileri ve belirteç imzalama belirteçte çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b580d-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="b580d-105">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="b580d-105">\<system.identityModel></span></span>  
<span data-ttu-id="b580d-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b580d-106">\<identityConfiguration></span></span>  
<span data-ttu-id="b580d-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b580d-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b580d-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b580d-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="b580d-109">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="b580d-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b580d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b580d-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b580d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b580d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b580d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b580d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b580d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b580d-113">Attributes</span></span>  
  
|<span data-ttu-id="b580d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b580d-114">Attribute</span></span>|<span data-ttu-id="b580d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b580d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b580d-116">türü</span><span class="sxs-lookup"><span data-stu-id="b580d-116">type</span></span>|<span data-ttu-id="b580d-117">Veren belirteç Çözümleyicisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b580d-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="b580d-118">Aşağıdakilerden biri olması gerekir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıf veya türeyen bir tür <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b580d-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="b580d-119">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b580d-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b580d-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b580d-120">Child Elements</span></span>  
 <span data-ttu-id="b580d-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="b580d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b580d-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b580d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b580d-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="b580d-123">Element</span></span>|<span data-ttu-id="b580d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b580d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b580d-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b580d-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="b580d-126">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b580d-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b580d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b580d-127">Remarks</span></span>  
 <span data-ttu-id="b580d-128">Veren belirteç Çözümleyicisi gelen iletileri ve belirteç imzalama belirteçte çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b580d-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="b580d-129">İmza denetimi için kullanılan şifreleme malzeme almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b580d-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="b580d-130">Belirtmeniz gerekir `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b580d-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="b580d-131">Belirtilen tür ya da olabilir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ya türetilen özel bir tür <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b580d-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="b580d-132">Bazı belirteci işleyicileri yapılandırmasında veren belirteç Çözümleyicisi ayarları belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b580d-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="b580d-133">Tek tek belirteç işleyicileri ayarları güvenlik belirteci işleyicisi koleksiyonda belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b580d-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b580d-134">Belirtme `<issuerTokenResolver>` öğesi bir alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak hala geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b580d-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="b580d-135">Ayarları `<securityTokenHandlerConfiguration>` öğesi geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="b580d-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b580d-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="b580d-136">Example</span></span>  
 <span data-ttu-id="b580d-137">Aşağıdaki XML türetilen özel bir sınıf dayalı bir veren belirteç Çözümleyicisi için yapılandırmasını gösterir <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="b580d-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="b580d-138">Bir özel yapılandırma öğesinden başlatılmış bir sözlük İzleyici anahtar çifti belirteç Çözümleyicisi tutar (`<AddAudienceKeyPair>`) sınıfı için tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="b580d-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="b580d-139">Sınıf geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> bu öğeyi işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="b580d-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="b580d-140">Geçersiz kılma aşağıdaki örnekte gösterilir; Ancak, bunu çağıran yöntemleri okumanızdır gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="b580d-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="b580d-141">Tam bir örnek için bkz: `CustomToken` örnek.</span><span class="sxs-lookup"><span data-stu-id="b580d-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="b580d-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="b580d-142">Example</span></span>  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b580d-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b580d-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
