---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 6e8267f170dbb26381564be7b66df5f617156885
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790448"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="7d986-101">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="7d986-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="7d986-102">İsteğe bağlı yapılandırma için sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="7d986-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="7d986-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7d986-103">\<system.identityModel></span></span>  
<span data-ttu-id="7d986-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7d986-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7d986-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="7d986-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="7d986-106">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="7d986-106">\<add></span></span>  
<span data-ttu-id="7d986-107">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="7d986-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d986-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d986-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d986-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d986-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7d986-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d986-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d986-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d986-111">Attributes</span></span>  
  
|<span data-ttu-id="7d986-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7d986-112">Attribute</span></span>|<span data-ttu-id="7d986-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d986-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d986-114">Certificatevalidationmode'u</span><span class="sxs-lookup"><span data-stu-id="7d986-114">certificateValidationMode</span></span>|<span data-ttu-id="7d986-115">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası için kullanılacak doğrulama modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7d986-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="7d986-116">"PeerOrChainTrust" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="7d986-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="7d986-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="7d986-117">mapToWindows</span></span>|<span data-ttu-id="7d986-118">Belirteci işleyicisi doğrulama belirteci için bir Windows hesabı gelen UPN Talebi kullanarak eşlemelisiniz olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d986-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="7d986-119">Varsayılan değer "false" dir.</span><span class="sxs-lookup"><span data-stu-id="7d986-119">The default is "false".</span></span>|  
|<span data-ttu-id="7d986-120">revocationMode</span><span class="sxs-lookup"><span data-stu-id="7d986-120">revocationMode</span></span>|<span data-ttu-id="7d986-121">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası için İptal modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7d986-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="7d986-122">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="7d986-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="7d986-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7d986-123">trustedStoreLocation</span></span>|<span data-ttu-id="7d986-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7d986-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="7d986-125">"LocalMachine" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="7d986-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="7d986-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="7d986-126">certificateValidator</span></span>|<span data-ttu-id="7d986-127">Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="7d986-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="7d986-128">Varsa `certificateValidationMode` özniteliktir "Özel", bu türden veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d986-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d986-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d986-129">Child Elements</span></span>  
 <span data-ttu-id="7d986-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d986-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d986-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d986-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7d986-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d986-132">Element</span></span>|<span data-ttu-id="7d986-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d986-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d986-134">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="7d986-134">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="7d986-135">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="7d986-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d986-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d986-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
