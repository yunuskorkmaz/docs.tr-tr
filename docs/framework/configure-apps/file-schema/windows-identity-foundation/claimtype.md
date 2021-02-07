---
description: 'Hakkında daha fazla bilgi edinin: <claimType>'
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 55fd32edc7fb810742c3cf678b434675aebba00e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664229"
---
# \<claimType>

<span data-ttu-id="54890-102">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="54890-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="54890-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="54890-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54890-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54890-104">Attributes and Elements</span></span>  

 <span data-ttu-id="54890-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54890-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54890-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54890-106">Attributes</span></span>  
  
|<span data-ttu-id="54890-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="54890-107">Attribute</span></span>|<span data-ttu-id="54890-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54890-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54890-109">tür</span><span class="sxs-lookup"><span data-stu-id="54890-109">type</span></span>|<span data-ttu-id="54890-110">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="54890-110">The claim type.</span></span> <span data-ttu-id="54890-111">Genellikle bir URI.</span><span class="sxs-lookup"><span data-stu-id="54890-111">Typically a URI.</span></span> <span data-ttu-id="54890-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54890-112">Required.</span></span>|  
|<span data-ttu-id="54890-113">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="54890-113">optional</span></span>|<span data-ttu-id="54890-114">Talep türünün isteğe bağlı olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="54890-114">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="54890-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="54890-115">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54890-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54890-116">Child Elements</span></span>  

 <span data-ttu-id="54890-117">Yok</span><span class="sxs-lookup"><span data-stu-id="54890-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54890-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54890-118">Parent Elements</span></span>  
  
|<span data-ttu-id="54890-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="54890-119">Element</span></span>|<span data-ttu-id="54890-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54890-120">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="54890-121">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="54890-121">Specifies the set of required claims for incoming security tokens.</span></span>|
