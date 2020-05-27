---
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
ms.openlocfilehash: 1572c206f4a5a5fe0fd189ca84d0bcda2249c6d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007656"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="2a4b5-102">CorMethodSemanticsAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2a4b5-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="2a4b5-103">Bir yöntem ile ilişkili bir özellik veya olay arasındaki ilişkiyi tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2a4b5-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a4b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a4b5-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2a4b5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2a4b5-105">Members</span></span>  
  
|<span data-ttu-id="2a4b5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2a4b5-106">Member</span></span>|<span data-ttu-id="2a4b5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a4b5-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="2a4b5-108">Metodun `set` bir özellik için erişimci olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a4b5-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="2a4b5-109">Metodun `get` bir özellik için erişimci olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a4b5-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="2a4b5-110">Metodun bir özellik veya burada tanımlananlardan farklı bir olayla ilişkisi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a4b5-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="2a4b5-111">Yöntemin bir olay için işleyici yöntemleri ekleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a4b5-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="2a4b5-112">Metodun bir olay için işleyici yöntemlerini kaldırdığından emin olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a4b5-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="2a4b5-113">Yöntemin bir olay harekete geçirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a4b5-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a4b5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a4b5-114">Requirements</span></span>  
 <span data-ttu-id="2a4b5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a4b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a4b5-116">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="2a4b5-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2a4b5-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a4b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4b5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a4b5-118">See also</span></span>

- [<span data-ttu-id="2a4b5-119">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="2a4b5-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
