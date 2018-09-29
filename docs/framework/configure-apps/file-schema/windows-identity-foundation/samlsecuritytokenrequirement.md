---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: c9856dae971691baf9dabe845bdecae90cbc8aa5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47455506"
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="06a00-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="06a00-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="06a00-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya türetilmiş bir sınıf ya da bu sınıflarının biri.</span><span class="sxs-lookup"><span data-stu-id="06a00-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="06a00-104">Tarafından temsil edilen <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="06a00-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="06a00-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="06a00-105">\<system.identityModel></span></span>  
<span data-ttu-id="06a00-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="06a00-106">\<identityConfiguration></span></span>  
<span data-ttu-id="06a00-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="06a00-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="06a00-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="06a00-108">\<add></span></span>  
<span data-ttu-id="06a00-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="06a00-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06a00-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06a00-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06a00-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="06a00-111">Attributes and Elements</span></span>  
 <span data-ttu-id="06a00-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06a00-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06a00-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06a00-113">Attributes</span></span>  
  
|<span data-ttu-id="06a00-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="06a00-114">Attribute</span></span>|<span data-ttu-id="06a00-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06a00-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06a00-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="06a00-116">mapToWindows</span></span>|<span data-ttu-id="06a00-117">Belirteci işleyicisi doğrulama belirteci için bir Windows hesabı gelen UPN Talebi kullanarak eşlemelisiniz olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06a00-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="06a00-118">Varsayılan değer "false" dir.</span><span class="sxs-lookup"><span data-stu-id="06a00-118">The default is "false".</span></span>|  
|<span data-ttu-id="06a00-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="06a00-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="06a00-120">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası için İptal modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="06a00-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="06a00-121">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="06a00-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="06a00-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="06a00-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="06a00-123">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası için kullanılacak doğrulama modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="06a00-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="06a00-124">"PeerOrChainTrust" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="06a00-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="06a00-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="06a00-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="06a00-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="06a00-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="06a00-127">"LocalMachine" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="06a00-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="06a00-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="06a00-128">issuerCertificateValidator</span></span>|<span data-ttu-id="06a00-129">Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="06a00-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="06a00-130">Varsa `issuerCertificateValidationMode` özniteliktir "Özel", bu türden veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06a00-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06a00-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="06a00-131">Child Elements</span></span>  
  
|<span data-ttu-id="06a00-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="06a00-132">Element</span></span>|<span data-ttu-id="06a00-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06a00-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06a00-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="06a00-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="06a00-135">Talep türünü belirleyen ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="06a00-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="06a00-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="06a00-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="06a00-137">Rol türü talep koleksiyonunda tanımlayan talep türünü belirtir <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06a00-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06a00-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="06a00-138">Parent Elements</span></span>  
  
|<span data-ttu-id="06a00-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="06a00-139">Element</span></span>|<span data-ttu-id="06a00-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06a00-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06a00-141">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="06a00-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="06a00-142">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="06a00-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06a00-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06a00-143">Remarks</span></span>  
 <span data-ttu-id="06a00-144">`<samlSecurityTokenRequirement>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> sınıfı nesne modelinde ve yapılandırmak için kullanılan `SamlSecurityTokenRequirement` özelliği bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="06a00-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06a00-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="06a00-145">Example</span></span>  
  
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
