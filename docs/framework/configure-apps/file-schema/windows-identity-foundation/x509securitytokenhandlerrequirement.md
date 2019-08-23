---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 2851820460a34d62175929b48ad57914df557059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945177"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="d0e15-101">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d0e15-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="d0e15-102"><xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0e15-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="d0e15-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d0e15-103">\<system.identityModel></span></span>  
<span data-ttu-id="d0e15-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d0e15-104">\<identityConfiguration></span></span>  
<span data-ttu-id="d0e15-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d0e15-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d0e15-106">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="d0e15-106">\<add></span></span>  
<span data-ttu-id="d0e15-107">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d0e15-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e15-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0e15-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0e15-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0e15-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d0e15-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0e15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0e15-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0e15-111">Attributes</span></span>  
  
|<span data-ttu-id="d0e15-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0e15-112">Attribute</span></span>|<span data-ttu-id="d0e15-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0e15-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0e15-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="d0e15-114">certificateValidationMode</span></span>|<span data-ttu-id="d0e15-115">X <xref:System.ServiceModel.Security.X509CertificateValidationMode> . 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0e15-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d0e15-116">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="d0e15-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="d0e15-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="d0e15-117">mapToWindows</span></span>|<span data-ttu-id="d0e15-118">Belirteç işleyicisinin, gelen UPN talebini kullanarak doğrulama belirtecini bir Windows hesabına eşlemenizi isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0e15-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="d0e15-119">Varsayılan değer "false" dır.</span><span class="sxs-lookup"><span data-stu-id="d0e15-119">The default is "false".</span></span>|  
|<span data-ttu-id="d0e15-120">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="d0e15-120">revocationMode</span></span>|<span data-ttu-id="d0e15-121">X <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0e15-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d0e15-122">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="d0e15-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="d0e15-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="d0e15-123">trustedStoreLocation</span></span>|<span data-ttu-id="d0e15-124">X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0e15-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="d0e15-125">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="d0e15-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="d0e15-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="d0e15-126">certificateValidator</span></span>|<span data-ttu-id="d0e15-127">Öğesinden <xref:System.IdentityModel.Selectors.X509CertificateValidator>türetilen özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="d0e15-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="d0e15-128">`certificateValidationMode` Öznitelik "Custom" ise, bu türün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0e15-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0e15-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0e15-129">Child Elements</span></span>  
 <span data-ttu-id="d0e15-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0e15-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0e15-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0e15-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d0e15-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0e15-132">Element</span></span>|<span data-ttu-id="d0e15-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0e15-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0e15-134">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="d0e15-134">\<add></span></span>](add.md)|<span data-ttu-id="d0e15-135">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="d0e15-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d0e15-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0e15-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
