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
ms.openlocfilehash: 288d7bfdf18be5cef032227c537032966fa68df4
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795709"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="e92a2-102">CorDebugStepReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e92a2-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="e92a2-103">Tek bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e92a2-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e92a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e92a2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e92a2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e92a2-105">Members</span></span>  
  
|<span data-ttu-id="e92a2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e92a2-106">Member</span></span>|<span data-ttu-id="e92a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e92a2-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="e92a2-108">Adımlama, aynı işlev içinde normal şekilde tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e92a2-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="e92a2-109">İşlev çağrıldıktan sonra normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="e92a2-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="e92a2-110">Yeni çağrılan bir işlevin başlangıcında, Adımlama normal şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="e92a2-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="e92a2-111">Bir özel durum oluşturuldu ve denetim bir özel durum filtresine geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e92a2-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="e92a2-112">Özel durum oluşturuldu ve denetim özel durum işleyicisine geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e92a2-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="e92a2-113">Denetim bir yakalayıcıyı geçti.</span><span class="sxs-lookup"><span data-stu-id="e92a2-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="e92a2-114">İş parçacığı, adım tamamlanmadan önce çıktı.</span><span class="sxs-lookup"><span data-stu-id="e92a2-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e92a2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e92a2-115">Requirements</span></span>  
 <span data-ttu-id="e92a2-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e92a2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e92a2-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e92a2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e92a2-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e92a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e92a2-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e92a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e92a2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e92a2-120">See also</span></span>

- [<span data-ttu-id="e92a2-121">StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e92a2-121">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="e92a2-122">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="e92a2-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
