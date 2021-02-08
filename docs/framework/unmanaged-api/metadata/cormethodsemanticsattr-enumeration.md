---
description: 'Daha fazla bilgi edinin: CorMethodSemanticsAttr numaralandırması'
title: CorMethodSemanticsAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 4079e81ae2389ff0684fd11d0751b191a7289932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784372"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="b3434-103">CorMethodSemanticsAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b3434-103">CorMethodSemanticsAttr Enumeration</span></span>

<span data-ttu-id="b3434-104">Bir yöntem ile ilişkili bir özellik veya olay arasındaki ilişkiyi tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b3434-104">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3434-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b3434-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="b3434-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b3434-106">Members</span></span>  
  
|<span data-ttu-id="b3434-107">Üye</span><span class="sxs-lookup"><span data-stu-id="b3434-107">Member</span></span>|<span data-ttu-id="b3434-108">Description</span><span class="sxs-lookup"><span data-stu-id="b3434-108">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="b3434-109">Metodun `set` bir özellik için erişimci olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3434-109">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="b3434-110">Metodun `get` bir özellik için erişimci olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3434-110">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="b3434-111">Metodun bir özellik veya burada tanımlananlardan farklı bir olayla ilişkisi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3434-111">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="b3434-112">Yöntemin bir olay için işleyici yöntemleri ekleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3434-112">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="b3434-113">Metodun bir olay için işleyici yöntemlerini kaldırdığından emin olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3434-113">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="b3434-114">Yöntemin bir olay harekete geçirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3434-114">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3434-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3434-115">Requirements</span></span>  

 <span data-ttu-id="b3434-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3434-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3434-117">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b3434-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b3434-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3434-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3434-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3434-119">See also</span></span>

- [<span data-ttu-id="b3434-120">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b3434-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
