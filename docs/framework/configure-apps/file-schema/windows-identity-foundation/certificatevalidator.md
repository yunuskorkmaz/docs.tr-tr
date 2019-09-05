---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 30f81dd5948a7d366c1116cffd347c85a396f5ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252119"
---
# <a name="certificatevalidator"></a><span data-ttu-id="87c3b-101">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="87c3b-101">\<certificateValidator></span></span>
<span data-ttu-id="87c3b-102">Sertifika doğrulaması için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="87c3b-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="87c3b-103">Bu tür yalnızca `certificateValidationMode` [ \<certificatevalidation >](certificatevalidation.md) öğesinin özniteliği "Custom" olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87c3b-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="87c3b-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87c3b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="87c3b-105">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="87c3b-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="87c3b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="87c3b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="87c3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<certificateValidation >** ](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="87c3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="87c3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidator >**</span><span class="sxs-lookup"><span data-stu-id="87c3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c3b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87c3b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87c3b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="87c3b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87c3b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87c3b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87c3b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87c3b-112">Attributes</span></span>  
  
|<span data-ttu-id="87c3b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87c3b-113">Attribute</span></span>|<span data-ttu-id="87c3b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87c3b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87c3b-115">türü</span><span class="sxs-lookup"><span data-stu-id="87c3b-115">type</span></span>|<span data-ttu-id="87c3b-116"><xref:System.IdentityModel.Selectors.X509CertificateValidator> Sınıfından türetilen özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="87c3b-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="87c3b-117">Bu türü kullanmak için [ \<certificatevalidation >](certificatevalidation.md) öğesinin özniteliğini"Custom"olarakayarlayın.`certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="87c3b-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="87c3b-118">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="87c3b-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="87c3b-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="87c3b-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87c3b-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="87c3b-120">Child Elements</span></span>  
 <span data-ttu-id="87c3b-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="87c3b-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87c3b-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="87c3b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="87c3b-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="87c3b-123">Element</span></span>|<span data-ttu-id="87c3b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87c3b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87c3b-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="87c3b-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="87c3b-126">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="87c3b-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87c3b-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="87c3b-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
