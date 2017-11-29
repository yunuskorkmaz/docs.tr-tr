---
title: "CorDebugExceptionObjectStackFrame Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionObjectStackFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionObjectStackFrame
helpviewer_keywords: CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf166f606aa2c0e0900356395c36bd6875897e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="48d58-102">CorDebugExceptionObjectStackFrame Yapısı</span><span class="sxs-lookup"><span data-stu-id="48d58-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="48d58-103">Bir özel durum nesnesi çerçeve bilgilerini temsil yığın.</span><span class="sxs-lookup"><span data-stu-id="48d58-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48d58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48d58-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="48d58-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="48d58-105">Members</span></span>  
  
|<span data-ttu-id="48d58-106">Üye</span><span class="sxs-lookup"><span data-stu-id="48d58-106">Member</span></span>|<span data-ttu-id="48d58-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48d58-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="48d58-108">Geçerli çerçevenin Icordebugmodule nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="48d58-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="48d58-109">Geçerli çerçevenin yönerge işaretçisi (EIP/RIP) değeri.</span><span class="sxs-lookup"><span data-stu-id="48d58-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="48d58-110">Geçerli çerçevenin yöntemi belirteci.</span><span class="sxs-lookup"><span data-stu-id="48d58-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="48d58-111">Çerçeve bir yabancı özel son çerçevede olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="48d58-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48d58-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48d58-112">Remarks</span></span>  
 <span data-ttu-id="48d58-113">Artık kullanımda olduğunda arayan Icordebugmodule nesnesine işaretçi serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48d58-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48d58-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48d58-114">Requirements</span></span>  
 <span data-ttu-id="48d58-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48d58-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48d58-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48d58-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48d58-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48d58-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48d58-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48d58-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d58-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48d58-119">See Also</span></span>  
 [<span data-ttu-id="48d58-120">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="48d58-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="48d58-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="48d58-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
