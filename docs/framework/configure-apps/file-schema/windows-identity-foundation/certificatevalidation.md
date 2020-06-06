---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252132"
---
# \<certificateValidation>
<span data-ttu-id="62582-101">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="62582-101">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="62582-102">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="62582-102">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="62582-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62582-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62582-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62582-104">Attributes and Elements</span></span>  
 <span data-ttu-id="62582-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62582-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62582-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62582-106">Attributes</span></span>  
  
|<span data-ttu-id="62582-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="62582-107">Attribute</span></span>|<span data-ttu-id="62582-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62582-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62582-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="62582-109">certificateValidationMode</span></span>|<span data-ttu-id="62582-110"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X. 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62582-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="62582-111">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="62582-111">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="62582-112">Özel bir doğrulayıcı belirtmek için, bu özniteliği "Custom" olarak ayarlayın ve öğesini kullanarak Doğrulayıcısı belirtin [\<certificateValidator>](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="62582-112">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="62582-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="62582-113">Optional.</span></span>|  
|<span data-ttu-id="62582-114">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="62582-114">revocationMode</span></span>|<span data-ttu-id="62582-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X. 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62582-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="62582-116">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="62582-116">The default value is "Online".</span></span> <span data-ttu-id="62582-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="62582-117">Optional.</span></span>|  
|<span data-ttu-id="62582-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="62582-118">trustedStoreLocation</span></span>|<span data-ttu-id="62582-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62582-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="62582-120">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="62582-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="62582-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="62582-121">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62582-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62582-122">Child Elements</span></span>  
  
|<span data-ttu-id="62582-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="62582-123">Element</span></span>|<span data-ttu-id="62582-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62582-124">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="62582-125">Sertifika doğrulaması için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="62582-125">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="62582-126">Bu tür yalnızca `certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) öğenin özniteliği "Custom" olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62582-126">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62582-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62582-127">Parent Elements</span></span>  
  
|<span data-ttu-id="62582-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="62582-128">Element</span></span>|<span data-ttu-id="62582-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62582-129">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="62582-130">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="62582-130">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="62582-131">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="62582-131">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62582-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62582-132">Remarks</span></span>  
 <span data-ttu-id="62582-133">Öğesi `<certificateValidation>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="62582-133">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="62582-134">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="62582-134">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="62582-135">Bazı belirteç işleyicileri, yapılandırmada sertifika doğrulama ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="62582-135">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="62582-136">Bağımsız belirteç işleyicilerindeki ayarlar, hem hizmet düzeyinde hem de güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="62582-136">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62582-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="62582-137">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
