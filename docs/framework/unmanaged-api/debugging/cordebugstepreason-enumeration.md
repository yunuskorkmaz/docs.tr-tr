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
ms.openlocfilehash: 92aee981aca3bac32c0ef264799e486315ca5103
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789249"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="e1a2c-102">CorDebugStepReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e1a2c-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="e1a2c-103">Tek bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1a2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1a2c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e1a2c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e1a2c-105">Members</span></span>  
  
|<span data-ttu-id="e1a2c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e1a2c-106">Member</span></span>|<span data-ttu-id="e1a2c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1a2c-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="e1a2c-108">Adımlama, aynı işlev içinde normal şekilde tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="e1a2c-109">İşlev çağrıldıktan sonra normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="e1a2c-110">Yeni çağrılan bir işlevin başlangıcında, Adımlama normal şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="e1a2c-111">Bir özel durum oluşturuldu ve denetim bir özel durum filtresine geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="e1a2c-112">Özel durum oluşturuldu ve denetim özel durum işleyicisine geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="e1a2c-113">Denetim bir yakalayıcıyı geçti.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="e1a2c-114">İş parçacığı, adım tamamlanmadan önce çıktı.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1a2c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1a2c-115">Requirements</span></span>  
 <span data-ttu-id="e1a2c-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1a2c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1a2c-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1a2c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1a2c-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1a2c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1a2c-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1a2c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a2c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1a2c-120">See also</span></span>

- [<span data-ttu-id="e1a2c-121">StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1a2c-121">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="e1a2c-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e1a2c-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
