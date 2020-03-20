---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152677"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="7e58d-101">\<verenTokenResolver></span><span class="sxs-lookup"><span data-stu-id="7e58d-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="7e58d-102">Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7e58d-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="7e58d-103">Veren belirteç çözümleyici, gelen belirteçler ve iletiler üzerinde imza belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e58d-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="7e58d-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7e58d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7e58d-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="7e58d-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="7e58d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="7e58d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="7e58d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="7e58d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="7e58d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="7e58d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="7e58d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<verenTokenResolver>**</span><span class="sxs-lookup"><span data-stu-id="7e58d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e58d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e58d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e58d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e58d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7e58d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e58d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e58d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e58d-113">Attributes</span></span>  
  
|<span data-ttu-id="7e58d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7e58d-114">Attribute</span></span>|<span data-ttu-id="7e58d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e58d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e58d-116">type</span><span class="sxs-lookup"><span data-stu-id="7e58d-116">type</span></span>|<span data-ttu-id="7e58d-117">Veren belirteç çözücünün türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e58d-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="7e58d-118"><xref:System.IdentityModel.Tokens.IssuerTokenResolver> Sınıf veya <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıftan türemiş bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e58d-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="7e58d-119">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7e58d-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e58d-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e58d-120">Child Elements</span></span>  
 <span data-ttu-id="7e58d-121">None</span><span class="sxs-lookup"><span data-stu-id="7e58d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e58d-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e58d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7e58d-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e58d-123">Element</span></span>|<span data-ttu-id="7e58d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e58d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e58d-125">\<güvenlikTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="7e58d-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="7e58d-126">Güvenlik belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e58d-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e58d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e58d-127">Remarks</span></span>  
 <span data-ttu-id="7e58d-128">Veren belirteç çözümleyici, gelen belirteçler ve iletiler üzerinde imza belirteci çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e58d-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="7e58d-129">İmzayı denetlemek için kullanılan şifreleme materyalini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e58d-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="7e58d-130">Özniteliği belirtmeniz `type` gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e58d-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="7e58d-131">Belirtilen tür, <xref:System.IdentityModel.Tokens.IssuerTokenResolver> <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıftan türeyen özel bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e58d-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="7e58d-132">Bazı belirteç işleyicileri, yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7e58d-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="7e58d-133">Tek tek belirteç işleyicileri ayarları, güvenlik belirteci işleyicisi koleksiyonunda belirtilenleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7e58d-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e58d-134">Kimlik Yapılandırma `<issuerTokenResolver>` [ \<>](identityconfiguration.md) öğesinin alt öğesi olarak öğebelirtilmesi küçümsenmiştir, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7e58d-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="7e58d-135">Öğedeki `<securityTokenHandlerConfiguration>` `<identityConfiguration>` ayarlar, öğedekiayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7e58d-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e58d-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e58d-136">Example</span></span>  
 <span data-ttu-id="7e58d-137">Aşağıdaki XML, 'den <xref:System.IdentityModel.Tokens.IssuerTokenResolver>türeyen özel bir sınıfa dayanan bir veren belirteç çözümleyicisi için yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e58d-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="7e58d-138">Belirteç çözümleyicisi, sınıf için tanımlanan özel bir yapılandırma öğesinden`<AddAudienceKeyPair>`( ) başharfe basılan hedef kitle anahtarı çiftlerinden oluşan bir sözlük tutar.</span><span class="sxs-lookup"><span data-stu-id="7e58d-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="7e58d-139">Sınıf, bu <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> öğeyi işlemek için yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7e58d-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="7e58d-140">Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak, adlandırdığı yöntemler kısalık için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="7e58d-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="7e58d-141">Tam örnek için, `CustomToken` örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="7e58d-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="7e58d-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e58d-142">Example</span></span>
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="7e58d-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e58d-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
