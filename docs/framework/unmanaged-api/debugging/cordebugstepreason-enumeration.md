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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71dcc34fd3489fc71cec4050b168548927833082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404537"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="e224e-102">CorDebugStepReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e224e-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="e224e-103">Tek bir adımı sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e224e-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e224e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e224e-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="e224e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e224e-105">Members</span></span>  
  
|<span data-ttu-id="e224e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e224e-106">Member</span></span>|<span data-ttu-id="e224e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e224e-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="e224e-108">Atlama normal olarak, aynı işlev içinde tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e224e-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="e224e-109">İşlev sonra atlama normal şekilde devam.</span><span class="sxs-lookup"><span data-stu-id="e224e-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="e224e-110">Atlama normal olarak, yeni çağrılan işlev başında devam eder.</span><span class="sxs-lookup"><span data-stu-id="e224e-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="e224e-111">Bir özel durum oluşturuldu ve denetim için bir özel durum filtresi geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e224e-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="e224e-112">Bir özel durum oluşturuldu ve denetim için bir özel durum işleyici geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e224e-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="e224e-113">Denetim bir dinleyiciyi geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e224e-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="e224e-114">Adım tamamlanmadan önce iş parçacığı çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="e224e-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e224e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e224e-115">Requirements</span></span>  
 <span data-ttu-id="e224e-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e224e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e224e-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e224e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e224e-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e224e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e224e-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e224e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e224e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e224e-120">See Also</span></span>  
 [<span data-ttu-id="e224e-121">StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e224e-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [<span data-ttu-id="e224e-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e224e-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
