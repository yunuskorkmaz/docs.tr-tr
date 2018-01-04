---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a642a79618329a55afa98dba04e4ac5f419cae7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="c92db-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="c92db-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="c92db-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="c92db-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="c92db-104">Tarafından temsil edilen <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c92db-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="c92db-105">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="c92db-105">\<system.identityModel></span></span>  
<span data-ttu-id="c92db-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="c92db-106">\<identityConfiguration></span></span>  
<span data-ttu-id="c92db-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="c92db-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="c92db-108">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c92db-108">\<add></span></span>  
<span data-ttu-id="c92db-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="c92db-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c92db-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c92db-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c92db-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c92db-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c92db-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c92db-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c92db-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c92db-113">Attributes</span></span>  
  
|<span data-ttu-id="c92db-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c92db-114">Attribute</span></span>|<span data-ttu-id="c92db-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c92db-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c92db-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="c92db-116">mapToWindows</span></span>|<span data-ttu-id="c92db-117">Belirteci işleyicisi Doğrulama belirtecini bir Windows hesabı gelen UPN Talebi kullanarak eşlemelisiniz olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c92db-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="c92db-118">Varsayılan değer "false" dir.</span><span class="sxs-lookup"><span data-stu-id="c92db-118">The default is "false".</span></span>|  
|<span data-ttu-id="c92db-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="c92db-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="c92db-120">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası kullanmak için İptali modu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="c92db-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="c92db-121">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="c92db-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="c92db-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="c92db-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="c92db-123">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası kullanmak için doğrulama modu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="c92db-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="c92db-124">Varsayılan değer "PeerOrChainTrust" dir.</span><span class="sxs-lookup"><span data-stu-id="c92db-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="c92db-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="c92db-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="c92db-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="c92db-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="c92db-127">Varsayılan değer "LocalMachine" dir.</span><span class="sxs-lookup"><span data-stu-id="c92db-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="c92db-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="c92db-128">issuerCertificateValidator</span></span>|<span data-ttu-id="c92db-129">Türetilen bir özel tür <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="c92db-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="c92db-130">Varsa `issuerCertificateValidationMode` özniteliği "Özel", bu türünün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c92db-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c92db-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c92db-131">Child Elements</span></span>  
  
|<span data-ttu-id="c92db-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="c92db-132">Element</span></span>|<span data-ttu-id="c92db-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c92db-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c92db-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="c92db-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="c92db-135">Belirtir talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c92db-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="c92db-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="c92db-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="c92db-137">Rol türü talepleri koleksiyonundaki tanımlar talep türünü belirten <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c92db-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c92db-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c92db-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c92db-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="c92db-139">Element</span></span>|<span data-ttu-id="c92db-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c92db-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c92db-141">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c92db-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="c92db-142">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="c92db-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c92db-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c92db-143">Remarks</span></span>  
 <span data-ttu-id="c92db-144">`<samlSecurityTokenRequirement>` Öğesi ile temsil edilir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> sınıf nesne modelinde ve yapılandırmak için kullanılan `SamlSecurityTokenRequirement` özelliği bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="c92db-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c92db-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="c92db-145">Example</span></span>  
  
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
