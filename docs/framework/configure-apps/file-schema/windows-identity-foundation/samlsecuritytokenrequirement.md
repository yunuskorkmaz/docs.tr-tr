---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: cab7572518a7a6dc26f8bbcf67cd424fa1c01085
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251898"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="85a84-101">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="85a84-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="85a84-102"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="85a84-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="85a84-103"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> Sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="85a84-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="85a84-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="85a84-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="85a84-105">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="85a84-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="85a84-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="85a84-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="85a84-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="85a84-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="85a84-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Ekle**](add.md)</span><span class="sxs-lookup"><span data-stu-id="85a84-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="85a84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<samlSecurityTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="85a84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85a84-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85a84-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85a84-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85a84-111">Attributes and Elements</span></span>  
 <span data-ttu-id="85a84-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85a84-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85a84-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85a84-113">Attributes</span></span>  
  
|<span data-ttu-id="85a84-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="85a84-114">Attribute</span></span>|<span data-ttu-id="85a84-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85a84-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85a84-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="85a84-116">mapToWindows</span></span>|<span data-ttu-id="85a84-117">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="85a84-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="85a84-118">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="85a84-118">The default is "false".</span></span>|  
|<span data-ttu-id="85a84-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="85a84-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="85a84-120">X <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="85a84-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="85a84-121">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="85a84-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="85a84-122">ıssuercertificatevalidationmode</span><span class="sxs-lookup"><span data-stu-id="85a84-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="85a84-123">X <xref:System.ServiceModel.Security.X509CertificateValidationMode> . 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="85a84-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="85a84-124">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="85a84-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="85a84-125">ıssuercertificatetrustedstorelocation</span><span class="sxs-lookup"><span data-stu-id="85a84-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="85a84-126">X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="85a84-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="85a84-127">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="85a84-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="85a84-128">ıssuercertificatevalidator</span><span class="sxs-lookup"><span data-stu-id="85a84-128">issuerCertificateValidator</span></span>|<span data-ttu-id="85a84-129">Öğesinden <xref:System.IdentityModel.Selectors.X509CertificateValidator>türetilen özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="85a84-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="85a84-130">`issuerCertificateValidationMode` Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85a84-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85a84-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85a84-131">Child Elements</span></span>  
  
|<span data-ttu-id="85a84-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="85a84-132">Element</span></span>|<span data-ttu-id="85a84-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85a84-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85a84-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="85a84-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="85a84-135"><xref:System.Security.Principal.IIdentity.Name%2A> Özelliği belirten talep türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="85a84-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="85a84-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="85a84-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="85a84-137">Belirteç işleyicisinin <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodu tarafından döndürülen nesneler koleksiyonundaki rol türü taleplerini tanımlayan talep türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="85a84-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85a84-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85a84-138">Parent Elements</span></span>  
  
|<span data-ttu-id="85a84-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="85a84-139">Element</span></span>|<span data-ttu-id="85a84-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85a84-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85a84-141">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="85a84-141">\<add></span></span>](add.md)|<span data-ttu-id="85a84-142">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="85a84-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85a84-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85a84-143">Remarks</span></span>  
 <span data-ttu-id="85a84-144"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Öğesi, nesne modelindeki sınıfı tarafından temsil edilir ve, veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>' de özelliği yapılandırmak için kullanılır. `<samlSecurityTokenRequirement>`</span><span class="sxs-lookup"><span data-stu-id="85a84-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85a84-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="85a84-145">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
