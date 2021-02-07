---
description: 'Daha fazla bilgi edinin: Cordebugghandlitype numaralandırması'
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
ms.openlocfilehash: 294fd7b04018331489e51d12930bcbbb81ec340a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662123"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="81a01-103">CorDebugHandleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="81a01-103">CorDebugHandleType Enumeration</span></span>

<span data-ttu-id="81a01-104">Tanıtıcı türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="81a01-104">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a01-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="81a01-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="81a01-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="81a01-106">Members</span></span>  
  
|<span data-ttu-id="81a01-107">Üye</span><span class="sxs-lookup"><span data-stu-id="81a01-107">Member</span></span>|<span data-ttu-id="81a01-108">Description</span><span class="sxs-lookup"><span data-stu-id="81a01-108">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="81a01-109">Tanıtıcı güçlü olduğundan, bir nesnenin çöp toplama tarafından geri kazanımasını önler.</span><span class="sxs-lookup"><span data-stu-id="81a01-109">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="81a01-110">Tanıtıcı zayıf, bu da bir nesnenin çöp toplama tarafından geri kazanımasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="81a01-110">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="81a01-111">Nesne toplandığında tanıtıcı geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="81a01-111">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81a01-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81a01-112">Requirements</span></span>  

 <span data-ttu-id="81a01-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81a01-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81a01-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81a01-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81a01-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="81a01-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81a01-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81a01-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a01-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81a01-117">See also</span></span>

- [<span data-ttu-id="81a01-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="81a01-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
