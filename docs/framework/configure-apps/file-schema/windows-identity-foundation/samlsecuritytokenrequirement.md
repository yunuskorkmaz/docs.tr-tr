---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: df259398beb242ea95efb248d6b5140b38ca3c45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942487"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="bf2ab-101">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="bf2ab-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="bf2ab-102"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="bf2ab-103"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> Sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="bf2ab-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bf2ab-104">\<system.identityModel></span></span>  
<span data-ttu-id="bf2ab-105">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bf2ab-105">\<identityConfiguration></span></span>  
<span data-ttu-id="bf2ab-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="bf2ab-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="bf2ab-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="bf2ab-107">\<add></span></span>  
<span data-ttu-id="bf2ab-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="bf2ab-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf2ab-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf2ab-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf2ab-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf2ab-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bf2ab-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf2ab-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf2ab-112">Attributes</span></span>  
  
|<span data-ttu-id="bf2ab-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bf2ab-113">Attribute</span></span>|<span data-ttu-id="bf2ab-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf2ab-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf2ab-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="bf2ab-115">mapToWindows</span></span>|<span data-ttu-id="bf2ab-116">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="bf2ab-117">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-117">The default is "false".</span></span>|  
|<span data-ttu-id="bf2ab-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="bf2ab-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="bf2ab-119">X <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="bf2ab-120">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="bf2ab-121">ıssuercertificatevalidationmode</span><span class="sxs-lookup"><span data-stu-id="bf2ab-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="bf2ab-122">X <xref:System.ServiceModel.Security.X509CertificateValidationMode> . 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="bf2ab-123">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="bf2ab-124">ıssuercertificatetrustedstorelocation</span><span class="sxs-lookup"><span data-stu-id="bf2ab-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="bf2ab-125">X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="bf2ab-126">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="bf2ab-127">ıssuercertificatevalidator</span><span class="sxs-lookup"><span data-stu-id="bf2ab-127">issuerCertificateValidator</span></span>|<span data-ttu-id="bf2ab-128">Öğesinden <xref:System.IdentityModel.Selectors.X509CertificateValidator>türetilen özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="bf2ab-129">`issuerCertificateValidationMode` Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf2ab-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf2ab-130">Child Elements</span></span>  
  
|<span data-ttu-id="bf2ab-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf2ab-131">Element</span></span>|<span data-ttu-id="bf2ab-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf2ab-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf2ab-133">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="bf2ab-133">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="bf2ab-134"><xref:System.Security.Principal.IIdentity.Name%2A> Özelliği belirten talep türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="bf2ab-135">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="bf2ab-135">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="bf2ab-136">Belirteç işleyicisinin <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodu tarafından döndürülen nesneler koleksiyonundaki rol türü taleplerini tanımlayan talep türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf2ab-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf2ab-137">Parent Elements</span></span>  
  
|<span data-ttu-id="bf2ab-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf2ab-138">Element</span></span>|<span data-ttu-id="bf2ab-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf2ab-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf2ab-140">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="bf2ab-140">\<add></span></span>](add.md)|<span data-ttu-id="bf2ab-141">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="bf2ab-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf2ab-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf2ab-142">Remarks</span></span>  
 <span data-ttu-id="bf2ab-143"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Öğesi, nesne modelindeki sınıfı tarafından temsil edilir ve, veya <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>' de özelliği yapılandırmak için kullanılır. `<samlSecurityTokenRequirement>`</span><span class="sxs-lookup"><span data-stu-id="bf2ab-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf2ab-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf2ab-144">Example</span></span>  
  
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
