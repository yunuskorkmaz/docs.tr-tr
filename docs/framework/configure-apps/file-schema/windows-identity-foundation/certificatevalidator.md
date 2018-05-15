---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a4663b0c3a2a6965a977a1d551c47de7e13d144b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="96b4c-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="96b4c-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="96b4c-103">Sertifika doğrulama için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="96b4c-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="96b4c-104">Bu tür yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) öğesi, "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="96b4c-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="96b4c-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="96b4c-105">\<system.identityModel></span></span>  
<span data-ttu-id="96b4c-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="96b4c-106">\<identityConfiguration></span></span>  
<span data-ttu-id="96b4c-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="96b4c-107">\<certificateValidation></span></span>  
<span data-ttu-id="96b4c-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="96b4c-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b4c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96b4c-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96b4c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="96b4c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="96b4c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96b4c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96b4c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="96b4c-112">Attributes</span></span>  
  
|<span data-ttu-id="96b4c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="96b4c-113">Attribute</span></span>|<span data-ttu-id="96b4c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96b4c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96b4c-115">türü</span><span class="sxs-lookup"><span data-stu-id="96b4c-115">type</span></span>|<span data-ttu-id="96b4c-116">Türetilen bir özel tür belirtir <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="96b4c-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="96b4c-117">Ayarlama `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) bu türünü kullanmak için "özel" öğesi.</span><span class="sxs-lookup"><span data-stu-id="96b4c-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="96b4c-118">Nasıl belirleneceği hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvuruları](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="96b4c-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="96b4c-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="96b4c-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96b4c-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="96b4c-120">Child Elements</span></span>  
 <span data-ttu-id="96b4c-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="96b4c-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96b4c-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="96b4c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="96b4c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="96b4c-123">Element</span></span>|<span data-ttu-id="96b4c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96b4c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96b4c-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="96b4c-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="96b4c-126">Sertifikaları doğrulamak için belirteci işleyicileri kullanma ayarlarını denetler.</span><span class="sxs-lookup"><span data-stu-id="96b4c-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96b4c-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="96b4c-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
