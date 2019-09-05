---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 76eeea635fd65486a1c16bea15a49018876dae99
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251689"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="f34c1-101">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="f34c1-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="f34c1-102"><xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f34c1-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="f34c1-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f34c1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f34c1-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f34c1-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f34c1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f34c1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f34c1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="f34c1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="f34c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Ekle**](add.md)</span><span class="sxs-lookup"><span data-stu-id="f34c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="f34c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<x509SecurityTokenHandlerRequirement >**</span><span class="sxs-lookup"><span data-stu-id="f34c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f34c1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f34c1-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f34c1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f34c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f34c1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f34c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f34c1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f34c1-112">Attributes</span></span>  
  
|<span data-ttu-id="f34c1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f34c1-113">Attribute</span></span>|<span data-ttu-id="f34c1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f34c1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f34c1-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="f34c1-115">certificateValidationMode</span></span>|<span data-ttu-id="f34c1-116">X <xref:System.ServiceModel.Security.X509CertificateValidationMode> . 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f34c1-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="f34c1-117">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="f34c1-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="f34c1-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="f34c1-118">mapToWindows</span></span>|<span data-ttu-id="f34c1-119">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f34c1-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="f34c1-120">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="f34c1-120">The default is "false".</span></span>|  
|<span data-ttu-id="f34c1-121">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="f34c1-121">revocationMode</span></span>|<span data-ttu-id="f34c1-122">X <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f34c1-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="f34c1-123">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="f34c1-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="f34c1-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="f34c1-124">trustedStoreLocation</span></span>|<span data-ttu-id="f34c1-125">X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f34c1-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="f34c1-126">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="f34c1-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="f34c1-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="f34c1-127">certificateValidator</span></span>|<span data-ttu-id="f34c1-128">Öğesinden <xref:System.IdentityModel.Selectors.X509CertificateValidator>türetilen özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="f34c1-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="f34c1-129">`certificateValidationMode` Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f34c1-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f34c1-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f34c1-130">Child Elements</span></span>  
 <span data-ttu-id="f34c1-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="f34c1-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f34c1-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f34c1-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f34c1-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="f34c1-133">Element</span></span>|<span data-ttu-id="f34c1-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f34c1-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f34c1-135">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="f34c1-135">\<add></span></span>](add.md)|<span data-ttu-id="f34c1-136">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="f34c1-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f34c1-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="f34c1-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
