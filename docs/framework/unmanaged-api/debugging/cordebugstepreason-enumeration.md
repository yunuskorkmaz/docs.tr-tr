---
description: 'Daha fazla bilgi edinin: CorDebugStepReason numaralandırması'
title: CorDebugStepReason Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 2a331b09709ffb6179f2e481baf4bf421d60ea99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801546"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="813c3-103">CorDebugStepReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="813c3-103">CorDebugStepReason Enumeration</span></span>

<span data-ttu-id="813c3-104">Tek bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="813c3-104">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813c3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="813c3-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="813c3-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="813c3-106">Members</span></span>  
  
|<span data-ttu-id="813c3-107">Üye</span><span class="sxs-lookup"><span data-stu-id="813c3-107">Member</span></span>|<span data-ttu-id="813c3-108">Description</span><span class="sxs-lookup"><span data-stu-id="813c3-108">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="813c3-109">Adımlama, aynı işlev içinde normal şekilde tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="813c3-109">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="813c3-110">İşlev çağrıldıktan sonra normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="813c3-110">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="813c3-111">Yeni çağrılan bir işlevin başlangıcında, Adımlama normal şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="813c3-111">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="813c3-112">Bir özel durum oluşturuldu ve denetim bir özel durum filtresine geçirildi.</span><span class="sxs-lookup"><span data-stu-id="813c3-112">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="813c3-113">Özel durum oluşturuldu ve denetim özel durum işleyicisine geçirildi.</span><span class="sxs-lookup"><span data-stu-id="813c3-113">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="813c3-114">Denetim bir yakalayıcıyı geçti.</span><span class="sxs-lookup"><span data-stu-id="813c3-114">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="813c3-115">İş parçacığı, adım tamamlanmadan önce çıktı.</span><span class="sxs-lookup"><span data-stu-id="813c3-115">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="813c3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="813c3-116">Requirements</span></span>  

 <span data-ttu-id="813c3-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="813c3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="813c3-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="813c3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="813c3-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="813c3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="813c3-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="813c3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813c3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="813c3-121">See also</span></span>

- [<span data-ttu-id="813c3-122">StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="813c3-122">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="813c3-123">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="813c3-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
