---
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
ms.openlocfilehash: 6c73afb00cbd104cff3d310d1369097b459c131e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133681"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="c50a5-102">CorDebugStepReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c50a5-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="c50a5-103">Tek bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c50a5-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c50a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c50a5-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c50a5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c50a5-105">Members</span></span>  
  
|<span data-ttu-id="c50a5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c50a5-106">Member</span></span>|<span data-ttu-id="c50a5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c50a5-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="c50a5-108">Adımlama, aynı işlev içinde normal şekilde tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c50a5-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="c50a5-109">İşlev çağrıldıktan sonra normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="c50a5-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="c50a5-110">Yeni çağrılan bir işlevin başlangıcında, Adımlama normal şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="c50a5-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="c50a5-111">Bir özel durum oluşturuldu ve denetim bir özel durum filtresine geçirildi.</span><span class="sxs-lookup"><span data-stu-id="c50a5-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="c50a5-112">Özel durum oluşturuldu ve denetim özel durum işleyicisine geçirildi.</span><span class="sxs-lookup"><span data-stu-id="c50a5-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="c50a5-113">Denetim bir yakalayıcıyı geçti.</span><span class="sxs-lookup"><span data-stu-id="c50a5-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="c50a5-114">İş parçacığı, adım tamamlanmadan önce çıktı.</span><span class="sxs-lookup"><span data-stu-id="c50a5-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c50a5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c50a5-115">Requirements</span></span>  
 <span data-ttu-id="c50a5-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c50a5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c50a5-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c50a5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c50a5-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c50a5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c50a5-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c50a5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c50a5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c50a5-120">See also</span></span>

- [<span data-ttu-id="c50a5-121">StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c50a5-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="c50a5-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c50a5-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
