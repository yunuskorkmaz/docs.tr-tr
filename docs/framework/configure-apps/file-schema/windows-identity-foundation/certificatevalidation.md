---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252132"
---
# <a name="certificatevalidation"></a><span data-ttu-id="ad525-101">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="ad525-101">\<certificateValidation></span></span>
<span data-ttu-id="ad525-102">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="ad525-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="ad525-103">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="ad525-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
<span data-ttu-id="ad525-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad525-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ad525-105">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ad525-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ad525-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ad525-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ad525-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidation >**</span><span class="sxs-lookup"><span data-stu-id="ad525-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad525-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad525-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad525-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad525-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ad525-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ad525-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad525-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ad525-111">Attributes</span></span>  
  
|<span data-ttu-id="ad525-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ad525-112">Attribute</span></span>|<span data-ttu-id="ad525-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad525-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad525-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="ad525-114">certificateValidationMode</span></span>|<span data-ttu-id="ad525-115">X <xref:System.ServiceModel.Security.X509CertificateValidationMode> . 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ad525-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="ad525-116">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="ad525-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="ad525-117">Özel bir doğrulayıcı belirtmek için, bu özniteliği "Custom" olarak ayarlayın ve [ \<CertificateValidator >](certificatevalidator.md) öğesini kullanarak Doğrulayıcısı belirtin.</span><span class="sxs-lookup"><span data-stu-id="ad525-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="ad525-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ad525-118">Optional.</span></span>|  
|<span data-ttu-id="ad525-119">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="ad525-119">revocationMode</span></span>|<span data-ttu-id="ad525-120">X <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ad525-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="ad525-121">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="ad525-121">The default value is "Online".</span></span> <span data-ttu-id="ad525-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ad525-122">Optional.</span></span>|  
|<span data-ttu-id="ad525-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="ad525-123">trustedStoreLocation</span></span>|<span data-ttu-id="ad525-124">X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ad525-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="ad525-125">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="ad525-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="ad525-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ad525-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad525-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad525-127">Child Elements</span></span>  
  
|<span data-ttu-id="ad525-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad525-128">Element</span></span>|<span data-ttu-id="ad525-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad525-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad525-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="ad525-130">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="ad525-131">Sertifika doğrulaması için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad525-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="ad525-132">Bu tür yalnızca `certificateValidationMode` [ \<certificatevalidation >](certificatevalidation.md) öğesinin özniteliği "Custom" olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ad525-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad525-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad525-133">Parent Elements</span></span>  
  
|<span data-ttu-id="ad525-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad525-134">Element</span></span>|<span data-ttu-id="ad525-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad525-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad525-136">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ad525-136">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="ad525-137">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad525-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="ad525-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ad525-138">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="ad525-139">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad525-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad525-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad525-140">Remarks</span></span>  
 <span data-ttu-id="ad525-141">Öğesi, `<identityConfiguration>` öğesinin altındaki hizmet düzeyinde veya öğesinin altındaki `<securityTokenHandlerConfiguration>` güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir. `<certificateValidation>`</span><span class="sxs-lookup"><span data-stu-id="ad525-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="ad525-142">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ad525-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="ad525-143">Bazı belirteç işleyicileri, yapılandırmada sertifika doğrulama ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ad525-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="ad525-144">Bağımsız belirteç işleyicilerindeki ayarlar, hem hizmet düzeyinde hem de güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ad525-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad525-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad525-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
