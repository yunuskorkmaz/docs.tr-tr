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
ms.openlocfilehash: 513fc93bdac71e2a3ba59ebb53fdde44f1659af5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220467"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="e45f9-102">CorDebugHandleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e45f9-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="e45f9-103">Tanıtıcı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e45f9-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e45f9-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="e45f9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e45f9-105">Members</span></span>  
  
|<span data-ttu-id="e45f9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e45f9-106">Member</span></span>|<span data-ttu-id="e45f9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e45f9-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="e45f9-108">Tanıtıcı güçlü, bir nesnenin çöp toplama tarafından iadesi engeller.</span><span class="sxs-lookup"><span data-stu-id="e45f9-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="e45f9-109">Tanıtıcı zayıf, hangi nesnenin çöp toplama tarafından iadesi engellemez.</span><span class="sxs-lookup"><span data-stu-id="e45f9-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="e45f9-110">Nesne toplandığında tanıtıcı geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e45f9-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e45f9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e45f9-111">Requirements</span></span>  
 <span data-ttu-id="e45f9-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e45f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e45f9-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e45f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e45f9-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e45f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e45f9-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e45f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e45f9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e45f9-116">See also</span></span>

- [<span data-ttu-id="e45f9-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e45f9-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
