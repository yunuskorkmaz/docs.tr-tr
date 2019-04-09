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
ms.openlocfilehash: 3ce2b23306e7e38f3982f8d5a4b377aa2f9547c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186257"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="2a883-102">CorDebugStepReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2a883-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="2a883-103">Bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a883-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a883-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a883-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2a883-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2a883-105">Members</span></span>  
  
|<span data-ttu-id="2a883-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2a883-106">Member</span></span>|<span data-ttu-id="2a883-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a883-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="2a883-108">Adımlama, normalde, aynı işlevin içinde tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2a883-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="2a883-109">İşlev sonra Adımlama normal olarak devam.</span><span class="sxs-lookup"><span data-stu-id="2a883-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="2a883-110">Adımlama normalde, yeni çağrılan bir işlevin başında devam eder.</span><span class="sxs-lookup"><span data-stu-id="2a883-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="2a883-111">Bir özel durum oluşturuldu ve özel durum filtresi için denetimi geçildi.</span><span class="sxs-lookup"><span data-stu-id="2a883-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="2a883-112">Bir özel durum oluşturuldu ve bir özel durum işleyicisine denetimi geçildi.</span><span class="sxs-lookup"><span data-stu-id="2a883-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="2a883-113">Denetim için bir dinleyiciyi geçirildi.</span><span class="sxs-lookup"><span data-stu-id="2a883-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="2a883-114">İş parçacığı adımı tamamlanmadan önce çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="2a883-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a883-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a883-115">Requirements</span></span>  
 <span data-ttu-id="2a883-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a883-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a883-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a883-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a883-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a883-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2a883-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2a883-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2a883-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a883-120">See also</span></span>

- [<span data-ttu-id="2a883-121">StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a883-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="2a883-122">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="2a883-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
