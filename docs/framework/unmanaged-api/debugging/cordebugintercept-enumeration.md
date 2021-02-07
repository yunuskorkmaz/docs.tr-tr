---
description: 'Daha fazla bilgi edinin: Cordebugkesmenoktası numaralandırması'
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
ms.openlocfilehash: ddd17aff309396fdcda37c731ff907224ee17db2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661980"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="29775-103">CorDebugIntercept Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="29775-103">CorDebugIntercept Enumeration</span></span>

<span data-ttu-id="29775-104">Ele geçirilebilecek kod türlerini gösterir (yani, ile).</span><span class="sxs-lookup"><span data-stu-id="29775-104">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29775-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="29775-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="29775-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="29775-106">Members</span></span>  
  
|<span data-ttu-id="29775-107">Üye</span><span class="sxs-lookup"><span data-stu-id="29775-107">Member</span></span>|<span data-ttu-id="29775-108">Description</span><span class="sxs-lookup"><span data-stu-id="29775-108">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="29775-109">Kod yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="29775-109">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="29775-110">Bir Oluşturucu yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="29775-110">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="29775-111">Özel durum filtresi yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="29775-111">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="29775-112">Güvenliği zorlayan kod yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="29775-112">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="29775-113">Bağlam ilkesi yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="29775-113">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="29775-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="29775-114">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="29775-115">Tüm kod yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="29775-115">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29775-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29775-116">Remarks</span></span>  

 <span data-ttu-id="29775-117">Ele geçirilebilecek kod türlerini oluşturmak için [ICorDebugStepper:: Setyakatmask](icordebugstepper-setinterceptmask-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29775-117">Use the [ICorDebugStepper::SetInterceptMask](icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29775-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29775-118">Requirements</span></span>  

 <span data-ttu-id="29775-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29775-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29775-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="29775-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29775-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="29775-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29775-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29775-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29775-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29775-123">See also</span></span>

- [<span data-ttu-id="29775-124">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="29775-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
