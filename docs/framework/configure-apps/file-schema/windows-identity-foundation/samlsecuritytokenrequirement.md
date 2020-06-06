---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152638"
---
# \<samlSecurityTokenRequirement>
<span data-ttu-id="6edd9-101"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Sınıf, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6edd9-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="6edd9-102">Sınıfı tarafından temsil edilir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="6edd9-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="6edd9-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6edd9-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6edd9-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6edd9-104">Attributes and Elements</span></span>  
 <span data-ttu-id="6edd9-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6edd9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6edd9-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6edd9-106">Attributes</span></span>  
  
|<span data-ttu-id="6edd9-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6edd9-107">Attribute</span></span>|<span data-ttu-id="6edd9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6edd9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6edd9-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="6edd9-109">mapToWindows</span></span>|<span data-ttu-id="6edd9-110">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6edd9-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="6edd9-111">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="6edd9-111">The default is "false".</span></span>|  
|<span data-ttu-id="6edd9-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="6edd9-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="6edd9-113"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X. 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6edd9-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="6edd9-114">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="6edd9-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="6edd9-115">ıssuercertificatevalidationmode</span><span class="sxs-lookup"><span data-stu-id="6edd9-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="6edd9-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X. 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6edd9-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="6edd9-117">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="6edd9-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="6edd9-118">ıssuercertificatetrustedstorelocation</span><span class="sxs-lookup"><span data-stu-id="6edd9-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="6edd9-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6edd9-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="6edd9-120">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="6edd9-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="6edd9-121">ıssuercertificatevalidator</span><span class="sxs-lookup"><span data-stu-id="6edd9-121">issuerCertificateValidator</span></span>|<span data-ttu-id="6edd9-122">Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="6edd9-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="6edd9-123">`issuerCertificateValidationMode`Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6edd9-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6edd9-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6edd9-124">Child Elements</span></span>  
  
|<span data-ttu-id="6edd9-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="6edd9-125">Element</span></span>|<span data-ttu-id="6edd9-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6edd9-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="6edd9-127">Özelliği belirten talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> .</span><span class="sxs-lookup"><span data-stu-id="6edd9-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="6edd9-128"><xref:System.Security.Claims.ClaimsIdentity>Belirteç işleyicisinin metodu tarafından döndürülen nesneler koleksiyonundaki rol türü taleplerini tanımlayan talep türünü belirtir <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> .</span><span class="sxs-lookup"><span data-stu-id="6edd9-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6edd9-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6edd9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="6edd9-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="6edd9-130">Element</span></span>|<span data-ttu-id="6edd9-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6edd9-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="6edd9-132">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="6edd9-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6edd9-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6edd9-133">Remarks</span></span>  
 <span data-ttu-id="6edd9-134">`<samlSecurityTokenRequirement>`Öğesi, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne modelindeki sınıfı tarafından temsil edilir ve, veya ' de özelliği yapılandırmak için kullanılır `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="6edd9-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6edd9-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="6edd9-135">Example</span></span>  
  
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
