---
title: "CorMethodSemanticsAttr Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodSemanticsAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodSemanticsAttr
helpviewer_keywords: CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c6dca24aad06b1c07c86cb716f4be344c8458471
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="b48fa-102">CorMethodSemanticsAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b48fa-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="b48fa-103">Bir yöntem ve bir ilişkili özelliğin veya olay arasındaki ilişkiyi tanımlayan değerler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b48fa-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b48fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b48fa-104">Syntax</span></span>  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="b48fa-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b48fa-105">Members</span></span>  
  
|<span data-ttu-id="b48fa-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b48fa-106">Member</span></span>|<span data-ttu-id="b48fa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b48fa-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="b48fa-108">Yöntemi gerektiğini belirten bir `set` bir özellik için erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="b48fa-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="b48fa-109">Yöntemi gerektiğini belirten bir `get` bir özellik için erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="b48fa-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="b48fa-110">Yöntemin bir özellik veya burada tanımlanan dışında bir olay için bir ilişki olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b48fa-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="b48fa-111">Yöntemi, bir olay işleyicisi yöntemlerini ekler belirtir.</span><span class="sxs-lookup"><span data-stu-id="b48fa-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="b48fa-112">Yöntemi, bir olay işleyicisi yöntemlerini kaldırır belirtir.</span><span class="sxs-lookup"><span data-stu-id="b48fa-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="b48fa-113">Yöntemin bir olay başlatır belirtir.</span><span class="sxs-lookup"><span data-stu-id="b48fa-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b48fa-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b48fa-114">Requirements</span></span>  
 <span data-ttu-id="b48fa-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b48fa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b48fa-116">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b48fa-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b48fa-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b48fa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48fa-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b48fa-118">See Also</span></span>  
 [<span data-ttu-id="b48fa-119">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b48fa-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
