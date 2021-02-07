---
description: 'Hakkında daha fazla bilgi edinin: <issuerTokenResolver>'
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 535b6f098e168a198eb0949d6baba6659e5140db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664099"
---
# \<issuerTokenResolver>

<span data-ttu-id="34cd1-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="34cd1-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="34cd1-103">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34cd1-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="34cd1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="34cd1-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34cd1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34cd1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="34cd1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34cd1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34cd1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34cd1-107">Attributes</span></span>  
  
|<span data-ttu-id="34cd1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34cd1-108">Attribute</span></span>|<span data-ttu-id="34cd1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34cd1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34cd1-110">tür</span><span class="sxs-lookup"><span data-stu-id="34cd1-110">type</span></span>|<span data-ttu-id="34cd1-111">Verenin belirteç Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="34cd1-111">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="34cd1-112">Sınıf <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ya da sınıftan türetilmiş bir tür olmalıdır <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="34cd1-112">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="34cd1-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="34cd1-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34cd1-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34cd1-114">Child Elements</span></span>  

 <span data-ttu-id="34cd1-115">Yok</span><span class="sxs-lookup"><span data-stu-id="34cd1-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34cd1-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34cd1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="34cd1-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="34cd1-117">Element</span></span>|<span data-ttu-id="34cd1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34cd1-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="34cd1-119">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="34cd1-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34cd1-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34cd1-120">Remarks</span></span>  

 <span data-ttu-id="34cd1-121">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34cd1-121">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="34cd1-122">İmzayı denetlemek için kullanılan şifreleme malzemesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34cd1-122">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="34cd1-123">Özniteliğini belirtmeniz gerekir `type` .</span><span class="sxs-lookup"><span data-stu-id="34cd1-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="34cd1-124">Belirtilen tür ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfından türetilen özel bir tür olabilir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="34cd1-124">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="34cd1-125">Bazı belirteç işleyicileri yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="34cd1-125">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="34cd1-126">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="34cd1-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34cd1-127">Öğenin `<issuerTokenResolver>` bir alt öğesi olarak belirtilmesi [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="34cd1-127">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="34cd1-128">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="34cd1-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34cd1-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="34cd1-129">Example</span></span>  

 <span data-ttu-id="34cd1-130">Aşağıdaki XML, ' den türetilen özel bir sınıfa dayalı bir veren belirteç Çözümleyicisi için yapılandırmayı gösterir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="34cd1-130">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="34cd1-131">Belirteç çözümleyici, sınıf için tanımlanan özel bir yapılandırma öğesinden () başlatılan bir hedef kitle anahtar çiftleri sözlüğü içerir `<AddAudienceKeyPair>` .</span><span class="sxs-lookup"><span data-stu-id="34cd1-131">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="34cd1-132">Sınıfı, <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> Bu öğeyi işlemek için yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="34cd1-132">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="34cd1-133">Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak çağrı yaptığı Yöntemler breçekimi için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="34cd1-133">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="34cd1-134">Tüm örnek için `CustomToken` örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="34cd1-134">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="34cd1-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="34cd1-135">Example</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="34cd1-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34cd1-136">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
