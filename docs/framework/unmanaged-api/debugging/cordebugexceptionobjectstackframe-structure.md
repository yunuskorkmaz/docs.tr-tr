---
title: "CorDebugExceptionObjectStackFrame Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f2d3f0d0c17c0fdf8b772ba38ae97fd8e406be8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="6eafe-102">CorDebugExceptionObjectStackFrame Yapısı</span><span class="sxs-lookup"><span data-stu-id="6eafe-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="6eafe-103">Bir özel durum nesnesi çerçeve bilgilerini temsil yığın.</span><span class="sxs-lookup"><span data-stu-id="6eafe-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eafe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6eafe-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="6eafe-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6eafe-105">Members</span></span>  
  
|<span data-ttu-id="6eafe-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6eafe-106">Member</span></span>|<span data-ttu-id="6eafe-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6eafe-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="6eafe-108">Geçerli çerçevenin Icordebugmodule nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6eafe-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="6eafe-109">Geçerli çerçevenin yönerge işaretçisi (EIP/RIP) değeri.</span><span class="sxs-lookup"><span data-stu-id="6eafe-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="6eafe-110">Geçerli çerçevenin yöntemi belirteci.</span><span class="sxs-lookup"><span data-stu-id="6eafe-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="6eafe-111">Çerçeve bir yabancı özel son çerçevede olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6eafe-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eafe-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6eafe-112">Remarks</span></span>  
 <span data-ttu-id="6eafe-113">Artık kullanımda olduğunda arayan Icordebugmodule nesnesine işaretçi serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6eafe-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eafe-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6eafe-114">Requirements</span></span>  
 <span data-ttu-id="6eafe-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eafe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eafe-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6eafe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6eafe-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6eafe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eafe-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eafe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eafe-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6eafe-119">See Also</span></span>  
 [<span data-ttu-id="6eafe-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="6eafe-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="6eafe-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6eafe-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
