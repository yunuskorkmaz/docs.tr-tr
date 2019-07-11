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
ms.openlocfilehash: 3d9dc94689083d79858319387747eb9dafe8b2f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739565"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="0dd35-102">CorDebugStepReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0dd35-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="0dd35-103">Bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dd35-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dd35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dd35-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0dd35-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0dd35-105">Members</span></span>  
  
|<span data-ttu-id="0dd35-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0dd35-106">Member</span></span>|<span data-ttu-id="0dd35-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dd35-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="0dd35-108">Adımlama, normalde, aynı işlevin içinde tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0dd35-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="0dd35-109">İşlev sonra Adımlama normal olarak devam.</span><span class="sxs-lookup"><span data-stu-id="0dd35-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="0dd35-110">Adımlama normalde, yeni çağrılan bir işlevin başında devam eder.</span><span class="sxs-lookup"><span data-stu-id="0dd35-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="0dd35-111">Bir özel durum oluşturuldu ve özel durum filtresi için denetimi geçildi.</span><span class="sxs-lookup"><span data-stu-id="0dd35-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="0dd35-112">Bir özel durum oluşturuldu ve bir özel durum işleyicisine denetimi geçildi.</span><span class="sxs-lookup"><span data-stu-id="0dd35-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="0dd35-113">Denetim için bir dinleyiciyi geçirildi.</span><span class="sxs-lookup"><span data-stu-id="0dd35-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="0dd35-114">İş parçacığı adımı tamamlanmadan önce çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="0dd35-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0dd35-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dd35-115">Requirements</span></span>  
 <span data-ttu-id="0dd35-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dd35-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dd35-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0dd35-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dd35-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dd35-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dd35-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dd35-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd35-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd35-120">See also</span></span>

- [<span data-ttu-id="0dd35-121">StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dd35-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="0dd35-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0dd35-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
