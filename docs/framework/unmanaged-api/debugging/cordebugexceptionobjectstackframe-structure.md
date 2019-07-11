---
title: CorDebugExceptionObjectStackFrame Yapısı
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cd2add7e96a8edaff8509563ae1846e80132001
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740092"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="e3900-102">CorDebugExceptionObjectStackFrame Yapısı</span><span class="sxs-lookup"><span data-stu-id="e3900-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="e3900-103">Temsil, çerçeve bilgileri bir özel durum nesnesinden yığın.</span><span class="sxs-lookup"><span data-stu-id="e3900-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3900-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3900-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="e3900-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e3900-105">Members</span></span>  
  
|<span data-ttu-id="e3900-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e3900-106">Member</span></span>|<span data-ttu-id="e3900-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3900-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="e3900-108">Geçerli çerçevenin Icordebugmodule nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e3900-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="e3900-109">Geçerli çerçevenin yönerge işaretçisi (EIP/RIP) değeri.</span><span class="sxs-lookup"><span data-stu-id="e3900-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="e3900-110">Geçerli çerçevenin yöntemi belirteç.</span><span class="sxs-lookup"><span data-stu-id="e3900-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="e3900-111">Çerçeve son kare yabancı bir özel durum olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e3900-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3900-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3900-112">Remarks</span></span>  
 <span data-ttu-id="e3900-113">Artık kullanımda olduğunda çağıran Icordebugmodule nesne işaretçisi serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3900-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3900-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3900-114">Requirements</span></span>  
 <span data-ttu-id="e3900-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3900-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3900-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3900-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3900-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3900-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3900-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3900-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3900-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3900-119">See also</span></span>

- [<span data-ttu-id="e3900-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e3900-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="e3900-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e3900-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
