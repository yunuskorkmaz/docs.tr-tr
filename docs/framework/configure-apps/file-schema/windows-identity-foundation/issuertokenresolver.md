---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 08082d2e6647f07f33df72ab79dac00c15a1cd1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791618"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="37ad5-101">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="37ad5-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="37ad5-102">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verici belirteç çözümleyici kaydeder.</span><span class="sxs-lookup"><span data-stu-id="37ad5-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="37ad5-103">Veren belirteç Çözümleyici, imzalama belirtecinin gelen belirteçleri ve iletileri çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37ad5-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="37ad5-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="37ad5-104">\<system.identityModel></span></span>  
<span data-ttu-id="37ad5-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37ad5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="37ad5-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="37ad5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="37ad5-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37ad5-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="37ad5-108">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="37ad5-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ad5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37ad5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37ad5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ad5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="37ad5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37ad5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37ad5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37ad5-112">Attributes</span></span>  
  
|<span data-ttu-id="37ad5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37ad5-113">Attribute</span></span>|<span data-ttu-id="37ad5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37ad5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37ad5-115">türü</span><span class="sxs-lookup"><span data-stu-id="37ad5-115">type</span></span>|<span data-ttu-id="37ad5-116">Veren belirteç çözümleyici türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="37ad5-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="37ad5-117">Aşağıdakilerden biri olması gereken <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı veya, türetilen tür <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="37ad5-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="37ad5-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="37ad5-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37ad5-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ad5-119">Child Elements</span></span>  
 <span data-ttu-id="37ad5-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="37ad5-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37ad5-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ad5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="37ad5-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="37ad5-122">Element</span></span>|<span data-ttu-id="37ad5-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37ad5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37ad5-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37ad5-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="37ad5-125">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="37ad5-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37ad5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37ad5-126">Remarks</span></span>  
 <span data-ttu-id="37ad5-127">Veren belirteç Çözümleyici, imzalama belirtecinin gelen belirteçleri ve iletileri çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37ad5-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="37ad5-128">İmzayı denetlemek için kullanılan şifreleme malzemelerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37ad5-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="37ad5-129">Belirtmelisiniz `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="37ad5-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="37ad5-130">Belirtilen türü olabilir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ya öğesinden türetilen özel bir tür <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="37ad5-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="37ad5-131">Bazı belirteç işleyicileri yapılandırmasında veren belirteç çözümleyici ayarları belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="37ad5-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="37ad5-132">Ayarları tek tek belirteç işleyicileri güvenlik belirteci işleyicisi koleksiyonda belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="37ad5-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37ad5-133">Belirtme `<issuerTokenResolver>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="37ad5-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="37ad5-134">Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="37ad5-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37ad5-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="37ad5-135">Example</span></span>  
 <span data-ttu-id="37ad5-136">Aşağıdaki XML yapılandırması için özel bir sınıf türetildiği temel alan bir veren belirteç çözümleyici gösterir <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="37ad5-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="37ad5-137">Belirteç Çözümleyici, bir özel yapılandırma öğesinden başlatılmış olan bir sözlük İzleyici anahtar çifti tutar (`<AddAudienceKeyPair>`) sınıfı için tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="37ad5-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="37ad5-138">Sınıf geçersiz kılmalarını <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> bu öğenin işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="37ad5-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="37ad5-139">Geçersiz kılma, aşağıdaki örnekte gösterilmiştir; Ancak, çağırdığı yöntemleri uzatmamak için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="37ad5-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="37ad5-140">Tam bir örnek için bkz `CustomToken` örnek.</span><span class="sxs-lookup"><span data-stu-id="37ad5-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="37ad5-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="37ad5-141">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37ad5-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37ad5-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
