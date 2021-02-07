---
description: 'Daha fazla bilgi edinin: CorDebugExceptionObjectStackFrame yapısı'
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
ms.openlocfilehash: abeb5a9f6385c494745a34c6f37d6fbc1376ad7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662162"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="107fa-103">CorDebugExceptionObjectStackFrame Yapısı</span><span class="sxs-lookup"><span data-stu-id="107fa-103">CorDebugExceptionObjectStackFrame Structure</span></span>

<span data-ttu-id="107fa-104">Bir özel durum nesnesinden yığın çerçeve bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="107fa-104">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107fa-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="107fa-105">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="107fa-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="107fa-106">Members</span></span>  
  
|<span data-ttu-id="107fa-107">Üye</span><span class="sxs-lookup"><span data-stu-id="107fa-107">Member</span></span>|<span data-ttu-id="107fa-108">Description</span><span class="sxs-lookup"><span data-stu-id="107fa-108">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="107fa-109">Geçerli çerçeve için ICorDebugModule nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="107fa-109">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="107fa-110">Geçerli çerçeveye ait yönerge işaretçisinin (EıP/RIP) değeri.</span><span class="sxs-lookup"><span data-stu-id="107fa-110">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="107fa-111">Geçerli çerçeve için yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="107fa-111">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="107fa-112">Karenin bir yabancı özel durumun son karesi olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="107fa-112">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="107fa-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="107fa-113">Remarks</span></span>  

 <span data-ttu-id="107fa-114">Çağıran, artık kullanımda olmadığında ICorDebugModule nesnesine işaretçiyi serbest bırakmalıdır.</span><span class="sxs-lookup"><span data-stu-id="107fa-114">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="107fa-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="107fa-115">Requirements</span></span>  

 <span data-ttu-id="107fa-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="107fa-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="107fa-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="107fa-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="107fa-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="107fa-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="107fa-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="107fa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107fa-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="107fa-120">See also</span></span>

- [<span data-ttu-id="107fa-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="107fa-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="107fa-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="107fa-122">Debugging</span></span>](index.md)
