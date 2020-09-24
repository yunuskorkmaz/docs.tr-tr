---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 1b5427210142c70c31c5f736c9b5e281dca53f33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150875"
---
# \<claimType>

<span data-ttu-id="10753-101">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="10753-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="10753-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="10753-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10753-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10753-103">Attributes and Elements</span></span>  

 <span data-ttu-id="10753-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10753-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10753-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10753-105">Attributes</span></span>  
  
|<span data-ttu-id="10753-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10753-106">Attribute</span></span>|<span data-ttu-id="10753-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10753-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10753-108">tür</span><span class="sxs-lookup"><span data-stu-id="10753-108">type</span></span>|<span data-ttu-id="10753-109">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="10753-109">The claim type.</span></span> <span data-ttu-id="10753-110">Genellikle bir URI.</span><span class="sxs-lookup"><span data-stu-id="10753-110">Typically a URI.</span></span> <span data-ttu-id="10753-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="10753-111">Required.</span></span>|  
|<span data-ttu-id="10753-112">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="10753-112">optional</span></span>|<span data-ttu-id="10753-113">Talep türünün isteğe bağlı olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="10753-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="10753-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="10753-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10753-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10753-115">Child Elements</span></span>  

 <span data-ttu-id="10753-116">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="10753-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10753-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10753-117">Parent Elements</span></span>  
  
|<span data-ttu-id="10753-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="10753-118">Element</span></span>|<span data-ttu-id="10753-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10753-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="10753-120">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10753-120">Specifies the set of required claims for incoming security tokens.</span></span>|
