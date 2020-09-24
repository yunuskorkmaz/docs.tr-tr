---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 9991430f09cb6a63d0a3cdde24a4ff03d3dd746d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165058"
---
# \<issuerNameRegistry>

<span data-ttu-id="9196e-101">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9196e-101">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="9196e-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="9196e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9196e-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9196e-103">Attributes and Elements</span></span>  

 <span data-ttu-id="9196e-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9196e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9196e-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9196e-105">Attributes</span></span>  
  
|<span data-ttu-id="9196e-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9196e-106">Attribute</span></span>|<span data-ttu-id="9196e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9196e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9196e-108">tür</span><span class="sxs-lookup"><span data-stu-id="9196e-108">type</span></span>|<span data-ttu-id="9196e-109">Sınıfından türeten bir tür <xref:System.IdentityModel.Tokens.IssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="9196e-109">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="9196e-110">Özel belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="9196e-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9196e-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9196e-111">Child Elements</span></span>  
  
|<span data-ttu-id="9196e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="9196e-112">Element</span></span>|<span data-ttu-id="9196e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9196e-113">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="9196e-114">Öznitelik, `type` yapılandırma tabanlı veren adı kayıt defterini ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı) belirttiğinde, [\<trustedIssuers>](trustedissuers.md) öğe belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9196e-114">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="9196e-115">[\<trustedIssuers>](trustedissuers.md)Öğesi `<add>` , `<clear>` `<remove>` alt öğeleri olarak, veya öğelerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="9196e-115">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9196e-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9196e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9196e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="9196e-117">Element</span></span>|<span data-ttu-id="9196e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9196e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="9196e-119">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9196e-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9196e-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9196e-120">Remarks</span></span>  

 <span data-ttu-id="9196e-121">Tüm verenin belirteçleri, bir veren adı kayıt defteri kullanılarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="9196e-121">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="9196e-122">Bu, sınıfından türetilen bir nesnedir <xref:System.IdentityModel.Tokens.IssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="9196e-122">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="9196e-123">Veren adı kayıt defteri, bir anımsatıcı adını, ilgili veren tarafından üretilen belirteçlerin imzalarını doğrulamak için gereken şifreleme malzemesiyle ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9196e-123">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="9196e-124">Veren adı kayıt defteri, bağlı olan taraf (RP) uygulaması tarafından güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="9196e-124">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="9196e-125">Veren adı kayıt defterinin türü, özniteliği kullanılarak belirtilir `type` .</span><span class="sxs-lookup"><span data-stu-id="9196e-125">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="9196e-126">`<issuerNameRegistry>`Öğe, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9196e-126">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="9196e-127">Yöntemi geçersiz kılarak bu alt öğeleri işleyen mantığı sağlarsınız <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> .</span><span class="sxs-lookup"><span data-stu-id="9196e-127">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="9196e-128">WıF, sınıfından tek bir veren adı kayıt defteri türü sağlar <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="9196e-128">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="9196e-129">Bu sınıf, yapılandırmada belirtilen bir güvenilen veren sertifikaları kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="9196e-129">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="9196e-130">Bu, `<trustedIssuers>` altında güvenilir veren sertifikaları koleksiyonunun yapılandırıldığı bir alt yapılandırma öğesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9196e-130">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="9196e-131">Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve `<add>` , veya öğeleri kullanılarak koleksiyona eklenir veya kaldırılır `<clear>` `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="9196e-131">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="9196e-132">`<issuerNameRegistry>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> .</span><span class="sxs-lookup"><span data-stu-id="9196e-132">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9196e-133">Öğenin `<issuerNameRegistry>` bir alt öğesi olarak belirtilmesi [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9196e-133">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="9196e-134">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="9196e-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9196e-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="9196e-135">Example</span></span>  

 <span data-ttu-id="9196e-136">Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9196e-136">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9196e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9196e-137">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
