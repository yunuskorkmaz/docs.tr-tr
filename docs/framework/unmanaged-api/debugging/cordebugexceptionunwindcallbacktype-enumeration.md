---
description: 'Şu konuda daha fazla bilgi edinin: Cordebugexceptionunwınbir CallbackType numaralandırması'
title: CorDebugExceptionUnwindCallbackType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
ms.openlocfilehash: 3e12cffcdf1eb921330f658215c52501dce83eff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747031"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="14f3c-103">CorDebugExceptionUnwindCallbackType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="14f3c-103">CorDebugExceptionUnwindCallbackType Enumeration</span></span>

<span data-ttu-id="14f3c-104">Geriye doğru izleme aşamasında geri çağırma tarafından sinyal edilen olayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="14f3c-104">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f3c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="14f3c-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="14f3c-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="14f3c-106">Members</span></span>  
  
|<span data-ttu-id="14f3c-107">Üye</span><span class="sxs-lookup"><span data-stu-id="14f3c-107">Member</span></span>|<span data-ttu-id="14f3c-108">Description</span><span class="sxs-lookup"><span data-stu-id="14f3c-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="14f3c-109">Geriye doğru izleme işleminin başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="14f3c-109">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="14f3c-110">Özel durum yakalanmıştı.</span><span class="sxs-lookup"><span data-stu-id="14f3c-110">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14f3c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14f3c-111">Requirements</span></span>  

 <span data-ttu-id="14f3c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14f3c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14f3c-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="14f3c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14f3c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="14f3c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14f3c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14f3c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14f3c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14f3c-116">See also</span></span>

- [<span data-ttu-id="14f3c-117">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="14f3c-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
