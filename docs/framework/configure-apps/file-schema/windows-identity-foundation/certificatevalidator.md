---
description: 'Hakkında daha fazla bilgi edinin: <certificateValidator>'
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 0b92eada916b239ca56342021bb958da6d02c2e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802170"
---
# \<certificateValidator>

<span data-ttu-id="ef07c-102">Sertifika doğrulaması için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef07c-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="ef07c-103">Bu tür yalnızca `certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) öğenin özniteliği "Custom" olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef07c-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="ef07c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef07c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef07c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef07c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ef07c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef07c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef07c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ef07c-107">Attributes</span></span>  
  
|<span data-ttu-id="ef07c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ef07c-108">Attribute</span></span>|<span data-ttu-id="ef07c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef07c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef07c-110">tür</span><span class="sxs-lookup"><span data-stu-id="ef07c-110">type</span></span>|<span data-ttu-id="ef07c-111">Sınıfından türetilen özel bir tür belirtir <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="ef07c-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="ef07c-112">`certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) Bu türü kullanmak için, öğesinin özniteliğini "Custom" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ef07c-112">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="ef07c-113">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef07c-113">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="ef07c-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ef07c-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef07c-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef07c-115">Child Elements</span></span>  

 <span data-ttu-id="ef07c-116">Yok</span><span class="sxs-lookup"><span data-stu-id="ef07c-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef07c-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef07c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ef07c-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef07c-118">Element</span></span>|<span data-ttu-id="ef07c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef07c-119">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="ef07c-120">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="ef07c-120">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef07c-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef07c-121">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
