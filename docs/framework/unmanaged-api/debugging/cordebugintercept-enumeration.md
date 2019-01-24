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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d15f34c55f0ee261c65649e9d431944201c546f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506036"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="245ba-102">CorDebugIntercept Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="245ba-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="245ba-103">(Bu, içine girdiğiniz olduğu gibi), geçirilebilir kod türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="245ba-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="245ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="245ba-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="245ba-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="245ba-105">Members</span></span>  
  
|<span data-ttu-id="245ba-106">Üye</span><span class="sxs-lookup"><span data-stu-id="245ba-106">Member</span></span>|<span data-ttu-id="245ba-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="245ba-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="245ba-108">Kod geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="245ba-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="245ba-109">Bir oluşturucu geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="245ba-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="245ba-110">Özel Durum Filtresi geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="245ba-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="245ba-111">Güvenlik uygulayan kod ele geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="245ba-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="245ba-112">Bir bağlam ilke geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="245ba-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="245ba-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="245ba-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="245ba-114">Tüm kod geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="245ba-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="245ba-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="245ba-115">Remarks</span></span>  
 <span data-ttu-id="245ba-116">Kullanım [ICorDebugStepper::setınterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) geçirilebilir kod türlerini oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="245ba-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="245ba-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="245ba-117">Requirements</span></span>  
 <span data-ttu-id="245ba-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="245ba-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="245ba-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="245ba-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="245ba-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="245ba-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="245ba-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="245ba-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245ba-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="245ba-122">See also</span></span>
- [<span data-ttu-id="245ba-123">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="245ba-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
