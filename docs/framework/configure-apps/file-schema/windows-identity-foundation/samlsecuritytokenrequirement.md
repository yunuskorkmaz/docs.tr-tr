---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152638"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="d3aa6-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d3aa6-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="d3aa6-102">Bu sınıflardan <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> herhangi <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> birinin sınıf, sınıf veya türetilmiş sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="d3aa6-103"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> Sınıf tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="d3aa6-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3aa6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3aa6-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d3aa6-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d3aa6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d3aa6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d3aa6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="d3aa6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="d3aa6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add.md)</span><span class="sxs-lookup"><span data-stu-id="d3aa6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="d3aa6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span><span class="sxs-lookup"><span data-stu-id="d3aa6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3aa6-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3aa6-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3aa6-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3aa6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d3aa6-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3aa6-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3aa6-113">Attributes</span></span>  
  
|<span data-ttu-id="d3aa6-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3aa6-114">Attribute</span></span>|<span data-ttu-id="d3aa6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3aa6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3aa6-116">haritaToWindows</span><span class="sxs-lookup"><span data-stu-id="d3aa6-116">mapToWindows</span></span>|<span data-ttu-id="d3aa6-117">Belirteç işleyicisinin gelen UPN talebini kullanarak doğrulama belirteciyle bir Windows hesabıyla eşlemesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="d3aa6-118">Varsayılan "false" olur.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-118">The default is "false".</span></span>|  
|<span data-ttu-id="d3aa6-119">verenSertifikaRevocationMode</span><span class="sxs-lookup"><span data-stu-id="d3aa6-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="d3aa6-120">X.509 sertifikası için kullanılacak iptal modunu belirten bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değer.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d3aa6-121">Varsayılan değer "Çevrimiçi"dir.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="d3aa6-122">verenSertifikaDoğrulamaModu</span><span class="sxs-lookup"><span data-stu-id="d3aa6-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="d3aa6-123">X.509 sertifikası için kullanılacak doğrulama modunu belirten bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> değer.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d3aa6-124">Varsayılan değer "PeerOrChainTrust"tır.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="d3aa6-125">verenSertifikaTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="d3aa6-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="d3aa6-126">X.509 sertifika deposunu belirten bir <xref:System.Security.Cryptography.X509Certificates.StoreLocation> değer.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="d3aa6-127">Varsayılan değer "LocalMachine"dir.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="d3aa6-128">verenSertifikaValidator</span><span class="sxs-lookup"><span data-stu-id="d3aa6-128">issuerCertificateValidator</span></span>|<span data-ttu-id="d3aa6-129">'den <xref:System.IdentityModel.Selectors.X509CertificateValidator>türeyen özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="d3aa6-130">`issuerCertificateValidationMode` Öznitelik "Özel" ise, bu tür bir örneği veren sertifika doğrulama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3aa6-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3aa6-131">Child Elements</span></span>  
  
|<span data-ttu-id="d3aa6-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3aa6-132">Element</span></span>|<span data-ttu-id="d3aa6-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3aa6-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3aa6-134">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="d3aa6-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="d3aa6-135"><xref:System.Security.Principal.IIdentity.Name%2A> Özelliği belirten talep türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="d3aa6-136">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="d3aa6-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="d3aa6-137">Belirteç işleyicisi <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> yöntemiyle döndürülen nesnelerin koleksiyonunda rol türü taleplerini tanımlayan talep türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3aa6-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3aa6-138">Parent Elements</span></span>  
  
|<span data-ttu-id="d3aa6-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3aa6-139">Element</span></span>|<span data-ttu-id="d3aa6-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3aa6-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3aa6-141">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="d3aa6-141">\<add></span></span>](add.md)|<span data-ttu-id="d3aa6-142">Belirteç işleyicisi koleksiyonuna belirtilen güvenlik belirteci işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="d3aa6-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3aa6-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3aa6-143">Remarks</span></span>  
 <span data-ttu-id="d3aa6-144">Öğe `<samlSecurityTokenRequirement>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> modelinde sınıf tarafından temsil edilir ve bir veya `SamlSecurityTokenRequirement` bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>özelliği yapılandırmak için kullanılır .</span><span class="sxs-lookup"><span data-stu-id="d3aa6-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3aa6-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3aa6-145">Example</span></span>  
  
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
