---
title: CorDebugHandleType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2898f530fe3f9368778d0f854e8254f7b32d5293
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404943"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="d3d2d-102">CorDebugHandleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d3d2d-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="d3d2d-103">Tanıtıcı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3d2d-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d2d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3d2d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="d3d2d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d3d2d-105">Members</span></span>  
  
|<span data-ttu-id="d3d2d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d3d2d-106">Member</span></span>|<span data-ttu-id="d3d2d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3d2d-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="d3d2d-108">Atık toplama tarafından iadesi nesneyi önleyen güçlü, işleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="d3d2d-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="d3d2d-109">İşleyici, bir nesne atık toplama tarafından iadesi engellemez, zayıftır.</span><span class="sxs-lookup"><span data-stu-id="d3d2d-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="d3d2d-110">Nesne toplandığında tanıtıcı geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="d3d2d-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3d2d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3d2d-111">Requirements</span></span>  
 <span data-ttu-id="d3d2d-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d2d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d2d-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3d2d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3d2d-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3d2d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3d2d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d2d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d2d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3d2d-116">See Also</span></span>  
 [<span data-ttu-id="d3d2d-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d3d2d-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
