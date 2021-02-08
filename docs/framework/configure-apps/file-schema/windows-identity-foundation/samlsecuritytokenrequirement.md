---
description: 'Hakkında daha fazla bilgi edinin: <samlSecurityTokenRequirement>'
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: 21e584480aae6f620e0809be77e02789536db426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786570"
---
# \<samlSecurityTokenRequirement>

<span data-ttu-id="e4436-102"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Sınıf, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4436-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="e4436-103">Sınıfı tarafından temsil edilir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="e4436-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="e4436-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e4436-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4436-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4436-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e4436-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4436-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4436-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4436-107">Attributes</span></span>  
  
|<span data-ttu-id="e4436-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e4436-108">Attribute</span></span>|<span data-ttu-id="e4436-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4436-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4436-110">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="e4436-110">mapToWindows</span></span>|<span data-ttu-id="e4436-111">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4436-111">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="e4436-112">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="e4436-112">The default is "false".</span></span>|  
|<span data-ttu-id="e4436-113">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="e4436-113">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="e4436-114"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X. 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e4436-114">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e4436-115">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="e4436-115">The default value is "Online".</span></span>|  
|<span data-ttu-id="e4436-116">ıssuercertificatevalidationmode</span><span class="sxs-lookup"><span data-stu-id="e4436-116">issuerCertificateValidationMode</span></span>|<span data-ttu-id="e4436-117"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X. 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e4436-117">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e4436-118">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="e4436-118">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="e4436-119">ıssuercertificatetrustedstorelocation</span><span class="sxs-lookup"><span data-stu-id="e4436-119">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="e4436-120"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e4436-120">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="e4436-121">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="e4436-121">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="e4436-122">ıssuercertificatevalidator</span><span class="sxs-lookup"><span data-stu-id="e4436-122">issuerCertificateValidator</span></span>|<span data-ttu-id="e4436-123">Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="e4436-123">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="e4436-124">`issuerCertificateValidationMode`Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4436-124">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4436-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4436-125">Child Elements</span></span>  
  
|<span data-ttu-id="e4436-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4436-126">Element</span></span>|<span data-ttu-id="e4436-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4436-127">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="e4436-128">Özelliği belirten talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> .</span><span class="sxs-lookup"><span data-stu-id="e4436-128">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="e4436-129"><xref:System.Security.Claims.ClaimsIdentity>Belirteç işleyicisinin metodu tarafından döndürülen nesneler koleksiyonundaki rol türü taleplerini tanımlayan talep türünü belirtir <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> .</span><span class="sxs-lookup"><span data-stu-id="e4436-129">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4436-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4436-130">Parent Elements</span></span>  
  
|<span data-ttu-id="e4436-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4436-131">Element</span></span>|<span data-ttu-id="e4436-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4436-132">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="e4436-133">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="e4436-133">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4436-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4436-134">Remarks</span></span>  

 <span data-ttu-id="e4436-135">`<samlSecurityTokenRequirement>`Öğesi, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne modelindeki sınıfı tarafından temsil edilir ve, veya ' de özelliği yapılandırmak için kullanılır `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="e4436-135">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4436-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4436-136">Example</span></span>  
  
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
