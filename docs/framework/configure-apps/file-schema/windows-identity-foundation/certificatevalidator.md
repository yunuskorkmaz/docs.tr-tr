---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: c25f183679f41f51ffee4f482bfe7a64763647d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941897"
---
# <a name="certificatevalidator"></a><span data-ttu-id="0d5f1-101">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="0d5f1-101">\<certificateValidator></span></span>
<span data-ttu-id="0d5f1-102">Sertifika doğrulaması için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d5f1-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="0d5f1-103">Bu tür yalnızca `certificateValidationMode` [ \<certificatevalidation >](certificatevalidation.md) öğesinin özniteliği "Custom" olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d5f1-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="0d5f1-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0d5f1-104">\<system.identityModel></span></span>  
<span data-ttu-id="0d5f1-105">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0d5f1-105">\<identityConfiguration></span></span>  
<span data-ttu-id="0d5f1-106">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="0d5f1-106">\<certificateValidation></span></span>  
<span data-ttu-id="0d5f1-107">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="0d5f1-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5f1-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d5f1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d5f1-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d5f1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0d5f1-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0d5f1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d5f1-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0d5f1-111">Attributes</span></span>  
  
|<span data-ttu-id="0d5f1-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0d5f1-112">Attribute</span></span>|<span data-ttu-id="0d5f1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d5f1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d5f1-114">türü</span><span class="sxs-lookup"><span data-stu-id="0d5f1-114">type</span></span>|<span data-ttu-id="0d5f1-115"><xref:System.IdentityModel.Selectors.X509CertificateValidator> Sınıfından türetilen özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d5f1-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="0d5f1-116">Bu türü kullanmak için [ \<certificatevalidation >](certificatevalidation.md) öğesinin özniteliğini"Custom"olarakayarlayın.`certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="0d5f1-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="0d5f1-117">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="0d5f1-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="0d5f1-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0d5f1-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d5f1-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d5f1-119">Child Elements</span></span>  
 <span data-ttu-id="0d5f1-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="0d5f1-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d5f1-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d5f1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0d5f1-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d5f1-122">Element</span></span>|<span data-ttu-id="0d5f1-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d5f1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d5f1-124">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="0d5f1-124">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="0d5f1-125">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="0d5f1-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0d5f1-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d5f1-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
