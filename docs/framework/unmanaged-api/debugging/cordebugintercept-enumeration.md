---
title: "CorDebugIntercept Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIntercept
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIntercept
helpviewer_keywords: CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7d34b5f1bdff7a7089d780645b91503a8464849
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="8ee75-102">CorDebugIntercept Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8ee75-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="8ee75-103">Tür (yani içine adım adım olan), geçirilebilir kod gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ee75-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ee75-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="8ee75-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8ee75-105">Members</span></span>  
  
|<span data-ttu-id="8ee75-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8ee75-106">Member</span></span>|<span data-ttu-id="8ee75-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ee75-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="8ee75-108">Kod geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ee75-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="8ee75-109">Bir oluşturucu geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ee75-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="8ee75-110">Bir özel durum filtresi geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ee75-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="8ee75-111">Güvenlik uygulayan kod ele geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ee75-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="8ee75-112">Bir bağlam İlkesi geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ee75-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="8ee75-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="8ee75-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="8ee75-114">Tüm kod geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ee75-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ee75-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ee75-115">Remarks</span></span>  
 <span data-ttu-id="8ee75-116">Kullanım [ICorDebugStepper::setınterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) geçirilebilir kod türlerini kurmaya yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ee75-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ee75-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ee75-117">Requirements</span></span>  
 <span data-ttu-id="8ee75-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee75-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee75-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ee75-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ee75-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ee75-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ee75-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ee75-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee75-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ee75-122">See Also</span></span>  
 [<span data-ttu-id="8ee75-123">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="8ee75-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
