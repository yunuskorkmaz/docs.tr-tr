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
ms.openlocfilehash: faa2082d31c5fa47b87e2238017066b477fdc191
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132169"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="15e36-102">CorDebugExceptionObjectStackFrame Yapısı</span><span class="sxs-lookup"><span data-stu-id="15e36-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="15e36-103">Bir özel durum nesnesinden yığın çerçeve bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="15e36-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e36-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15e36-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="15e36-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="15e36-105">Members</span></span>  
  
|<span data-ttu-id="15e36-106">Üye</span><span class="sxs-lookup"><span data-stu-id="15e36-106">Member</span></span>|<span data-ttu-id="15e36-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15e36-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="15e36-108">Geçerli çerçeve için ICorDebugModule nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="15e36-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="15e36-109">Geçerli çerçeveye ait yönerge işaretçisinin (EıP/RIP) değeri.</span><span class="sxs-lookup"><span data-stu-id="15e36-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="15e36-110">Geçerli çerçeve için yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="15e36-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="15e36-111">Karenin bir yabancı özel durumun son karesi olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="15e36-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15e36-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15e36-112">Remarks</span></span>  
 <span data-ttu-id="15e36-113">Çağıran, artık kullanımda olmadığında ICorDebugModule nesnesine işaretçiyi serbest bırakmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15e36-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e36-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15e36-114">Requirements</span></span>  
 <span data-ttu-id="15e36-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15e36-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e36-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="15e36-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15e36-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="15e36-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15e36-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15e36-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e36-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15e36-119">See also</span></span>

- [<span data-ttu-id="15e36-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="15e36-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="15e36-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="15e36-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
