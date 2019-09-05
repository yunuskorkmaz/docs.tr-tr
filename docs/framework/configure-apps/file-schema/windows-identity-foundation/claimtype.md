---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252065"
---
# <a name="claimtype"></a><span data-ttu-id="ed343-101">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="ed343-101">\<claimType></span></span>
<span data-ttu-id="ed343-102">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed343-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
<span data-ttu-id="ed343-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed343-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed343-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ed343-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ed343-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ed343-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ed343-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequired >** ](claimtyperequired.md)</span><span class="sxs-lookup"><span data-stu-id="ed343-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)</span></span>\  
<span data-ttu-id="ed343-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimType >**</span><span class="sxs-lookup"><span data-stu-id="ed343-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed343-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed343-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed343-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed343-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ed343-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed343-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed343-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed343-111">Attributes</span></span>  
  
|<span data-ttu-id="ed343-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ed343-112">Attribute</span></span>|<span data-ttu-id="ed343-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed343-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed343-114">türü</span><span class="sxs-lookup"><span data-stu-id="ed343-114">type</span></span>|<span data-ttu-id="ed343-115">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="ed343-115">The claim type.</span></span> <span data-ttu-id="ed343-116">Genellikle bir URI.</span><span class="sxs-lookup"><span data-stu-id="ed343-116">Typically a URI.</span></span> <span data-ttu-id="ed343-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ed343-117">Required.</span></span>|  
|<span data-ttu-id="ed343-118">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="ed343-118">optional</span></span>|<span data-ttu-id="ed343-119">Talep türünün isteğe bağlı olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="ed343-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="ed343-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ed343-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed343-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed343-121">Child Elements</span></span>  
 <span data-ttu-id="ed343-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="ed343-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed343-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed343-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ed343-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed343-124">Element</span></span>|<span data-ttu-id="ed343-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed343-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed343-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="ed343-126">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="ed343-127">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed343-127">Specifies the set of required claims for incoming security tokens.</span></span>|
