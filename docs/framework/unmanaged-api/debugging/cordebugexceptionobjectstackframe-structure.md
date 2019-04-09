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
ms.openlocfilehash: 5a4cd4d353c22921ed3dba1dc08fe2cee7e429f8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173088"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="bd192-102">CorDebugExceptionObjectStackFrame Yapısı</span><span class="sxs-lookup"><span data-stu-id="bd192-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="bd192-103">Temsil, çerçeve bilgileri bir özel durum nesnesinden yığın.</span><span class="sxs-lookup"><span data-stu-id="bd192-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd192-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd192-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="bd192-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bd192-105">Members</span></span>  
  
|<span data-ttu-id="bd192-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bd192-106">Member</span></span>|<span data-ttu-id="bd192-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd192-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="bd192-108">Geçerli çerçevenin Icordebugmodule nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bd192-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="bd192-109">Geçerli çerçevenin yönerge işaretçisi (EIP/RIP) değeri.</span><span class="sxs-lookup"><span data-stu-id="bd192-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="bd192-110">Geçerli çerçevenin yöntemi belirteç.</span><span class="sxs-lookup"><span data-stu-id="bd192-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="bd192-111">Çerçeve son kare yabancı bir özel durum olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bd192-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd192-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd192-112">Remarks</span></span>  
 <span data-ttu-id="bd192-113">Artık kullanımda olduğunda çağıran Icordebugmodule nesne işaretçisi serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd192-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd192-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd192-114">Requirements</span></span>  
 <span data-ttu-id="bd192-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd192-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd192-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd192-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd192-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd192-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bd192-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bd192-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd192-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd192-119">See also</span></span>

- [<span data-ttu-id="bd192-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="bd192-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="bd192-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bd192-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
