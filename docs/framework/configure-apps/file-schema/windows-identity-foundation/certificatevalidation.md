---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 8185153eb02c5794b0f6ac02a6837806f2073c07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941915"
---
# <a name="certificatevalidation"></a><span data-ttu-id="a96d2-101">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="a96d2-101">\<certificateValidation></span></span>
<span data-ttu-id="a96d2-102">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="a96d2-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="a96d2-103">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="a96d2-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="a96d2-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a96d2-104">\<system.identityModel></span></span>  
<span data-ttu-id="a96d2-105">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a96d2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a96d2-106">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="a96d2-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a96d2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a96d2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a96d2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a96d2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a96d2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a96d2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a96d2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a96d2-110">Attributes</span></span>  
  
|<span data-ttu-id="a96d2-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a96d2-111">Attribute</span></span>|<span data-ttu-id="a96d2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a96d2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a96d2-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a96d2-113">certificateValidationMode</span></span>|<span data-ttu-id="a96d2-114">X <xref:System.ServiceModel.Security.X509CertificateValidationMode> . 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a96d2-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="a96d2-115">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="a96d2-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="a96d2-116">Özel bir doğrulayıcı belirtmek için, bu özniteliği "Custom" olarak ayarlayın ve [ \<CertificateValidator >](certificatevalidator.md) öğesini kullanarak Doğrulayıcısı belirtin.</span><span class="sxs-lookup"><span data-stu-id="a96d2-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="a96d2-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a96d2-117">Optional.</span></span>|  
|<span data-ttu-id="a96d2-118">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="a96d2-118">revocationMode</span></span>|<span data-ttu-id="a96d2-119">X <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a96d2-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="a96d2-120">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="a96d2-120">The default value is "Online".</span></span> <span data-ttu-id="a96d2-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a96d2-121">Optional.</span></span>|  
|<span data-ttu-id="a96d2-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a96d2-122">trustedStoreLocation</span></span>|<span data-ttu-id="a96d2-123">X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a96d2-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="a96d2-124">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="a96d2-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="a96d2-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a96d2-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a96d2-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a96d2-126">Child Elements</span></span>  
  
|<span data-ttu-id="a96d2-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="a96d2-127">Element</span></span>|<span data-ttu-id="a96d2-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a96d2-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a96d2-129">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="a96d2-129">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="a96d2-130">Sertifika doğrulaması için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="a96d2-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="a96d2-131">Bu tür yalnızca `certificateValidationMode` [ \<certificatevalidation >](certificatevalidation.md) öğesinin özniteliği "Custom" olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a96d2-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a96d2-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a96d2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="a96d2-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="a96d2-133">Element</span></span>|<span data-ttu-id="a96d2-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a96d2-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a96d2-135">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a96d2-135">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="a96d2-136">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a96d2-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="a96d2-137">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a96d2-137">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a96d2-138">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a96d2-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a96d2-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a96d2-139">Remarks</span></span>  
 <span data-ttu-id="a96d2-140">Öğesi, `<identityConfiguration>` öğesinin altındaki hizmet düzeyinde veya öğesinin altındaki `<securityTokenHandlerConfiguration>` güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir. `<certificateValidation>`</span><span class="sxs-lookup"><span data-stu-id="a96d2-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="a96d2-141">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a96d2-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="a96d2-142">Bazı belirteç işleyicileri, yapılandırmada sertifika doğrulama ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a96d2-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="a96d2-143">Bağımsız belirteç işleyicilerindeki ayarlar, hem hizmet düzeyinde hem de güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a96d2-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a96d2-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="a96d2-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
