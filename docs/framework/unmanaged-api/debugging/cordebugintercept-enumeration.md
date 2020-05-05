---
title: CorDebugIntercept Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: 18a5e337b6026a20a95b1c29f3d7bda5187efc66
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795888"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="295e7-102">CorDebugIntercept Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="295e7-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="295e7-103">Ele geçirilebilecek kod türlerini gösterir (yani, ile).</span><span class="sxs-lookup"><span data-stu-id="295e7-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="295e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="295e7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="295e7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="295e7-105">Members</span></span>  
  
|<span data-ttu-id="295e7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="295e7-106">Member</span></span>|<span data-ttu-id="295e7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="295e7-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="295e7-108">Kod yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="295e7-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="295e7-109">Bir Oluşturucu yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="295e7-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="295e7-110">Özel durum filtresi yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="295e7-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="295e7-111">Güvenliği zorlayan kod yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="295e7-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="295e7-112">Bağlam ilkesi yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="295e7-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="295e7-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="295e7-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="295e7-114">Tüm kod yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="295e7-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="295e7-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="295e7-115">Remarks</span></span>  
 <span data-ttu-id="295e7-116">Ele geçirilebilecek kod türlerini oluşturmak için [ICorDebugStepper:: Setyakatmask](icordebugstepper-setinterceptmask-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="295e7-116">Use the [ICorDebugStepper::SetInterceptMask](icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="295e7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="295e7-117">Requirements</span></span>  
 <span data-ttu-id="295e7-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="295e7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="295e7-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="295e7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="295e7-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="295e7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="295e7-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="295e7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="295e7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="295e7-122">See also</span></span>

- [<span data-ttu-id="295e7-123">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="295e7-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
