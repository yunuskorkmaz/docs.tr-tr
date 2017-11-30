---
title: '&lt;certificateValidation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 778088f2e0508f5a80c29ae027b2442a80286795
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="2e0db-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="2e0db-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="2e0db-103">Sertifikaları doğrulamak için belirteci işleyicileri kullanma ayarlarını denetler.</span><span class="sxs-lookup"><span data-stu-id="2e0db-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="2e0db-104">Belirli bir işleyici ile kendi Doğrulayıcı yapılandırdıysanız bu ayarları geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="2e0db-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="2e0db-105">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="2e0db-105">\<system.identityModel></span></span>  
<span data-ttu-id="2e0db-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2e0db-106">\<identityConfiguration></span></span>  
<span data-ttu-id="2e0db-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="2e0db-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0db-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e0db-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e0db-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e0db-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2e0db-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e0db-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e0db-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2e0db-111">Attributes</span></span>  
  
|<span data-ttu-id="2e0db-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2e0db-112">Attribute</span></span>|<span data-ttu-id="2e0db-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e0db-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2e0db-114">certificateValidationMode değerini</span><span class="sxs-lookup"><span data-stu-id="2e0db-114">certificateValidationMode</span></span>|<span data-ttu-id="2e0db-115">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası kullanmak için doğrulama modu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2e0db-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="2e0db-116">Varsayılan değer "PeerOrChainTrust" dir.</span><span class="sxs-lookup"><span data-stu-id="2e0db-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="2e0db-117">Özel Doğrulayıcı sağlayıcısı belirtmek için bu özniteliği "Özel" olarak ayarlanmış ve kullanarak Doğrulayıcı belirtin [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e0db-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="2e0db-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2e0db-118">Optional.</span></span>|  
|<span data-ttu-id="2e0db-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="2e0db-119">revocationMode</span></span>|<span data-ttu-id="2e0db-120">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası kullanmak için İptali modu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2e0db-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="2e0db-121">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="2e0db-121">The default value is "Online".</span></span> <span data-ttu-id="2e0db-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2e0db-122">Optional.</span></span>|  
|<span data-ttu-id="2e0db-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="2e0db-123">trustedStoreLocation</span></span>|<span data-ttu-id="2e0db-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2e0db-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="2e0db-125">Varsayılan değer "LocalMachine" dir.</span><span class="sxs-lookup"><span data-stu-id="2e0db-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="2e0db-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2e0db-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e0db-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e0db-127">Child Elements</span></span>  
  
|<span data-ttu-id="2e0db-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e0db-128">Element</span></span>|<span data-ttu-id="2e0db-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e0db-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e0db-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="2e0db-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="2e0db-131">Sertifika doğrulama için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e0db-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="2e0db-132">Bu tür yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) öğesi, "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2e0db-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e0db-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e0db-133">Parent Elements</span></span>  
  
|<span data-ttu-id="2e0db-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e0db-134">Element</span></span>|<span data-ttu-id="2e0db-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e0db-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e0db-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2e0db-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="2e0db-137">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e0db-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="2e0db-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2e0db-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="2e0db-139">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e0db-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e0db-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e0db-140">Remarks</span></span>  
 <span data-ttu-id="2e0db-141">A `<certificateValidation>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyinde altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e0db-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="2e0db-142">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2e0db-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="2e0db-143">Bazı belirteci işleyicileri yapılandırmasında sertifika doğrulama ayarları belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e0db-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="2e0db-144">Ayarları tek tek belirteç işleyicileri belirtilen hizmet düzeyinde ve güvenlik belirteci işleyicisi koleksiyonu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2e0db-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e0db-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e0db-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
