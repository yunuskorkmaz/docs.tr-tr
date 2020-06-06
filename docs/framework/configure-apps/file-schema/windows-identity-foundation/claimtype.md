---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252065"
---
# \<claimType>
<span data-ttu-id="6b2eb-101">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b2eb-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="6b2eb-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b2eb-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b2eb-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2eb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6b2eb-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b2eb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b2eb-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b2eb-105">Attributes</span></span>  
  
|<span data-ttu-id="6b2eb-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6b2eb-106">Attribute</span></span>|<span data-ttu-id="6b2eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b2eb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b2eb-108">tür</span><span class="sxs-lookup"><span data-stu-id="6b2eb-108">type</span></span>|<span data-ttu-id="6b2eb-109">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="6b2eb-109">The claim type.</span></span> <span data-ttu-id="6b2eb-110">Genellikle bir URI.</span><span class="sxs-lookup"><span data-stu-id="6b2eb-110">Typically a URI.</span></span> <span data-ttu-id="6b2eb-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6b2eb-111">Required.</span></span>|  
|<span data-ttu-id="6b2eb-112">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="6b2eb-112">optional</span></span>|<span data-ttu-id="6b2eb-113">Talep türünün isteğe bağlı olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="6b2eb-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="6b2eb-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6b2eb-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b2eb-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2eb-115">Child Elements</span></span>  
 <span data-ttu-id="6b2eb-116">Yok</span><span class="sxs-lookup"><span data-stu-id="6b2eb-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b2eb-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2eb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6b2eb-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b2eb-118">Element</span></span>|<span data-ttu-id="6b2eb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b2eb-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="6b2eb-120">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b2eb-120">Specifies the set of required claims for incoming security tokens.</span></span>|
