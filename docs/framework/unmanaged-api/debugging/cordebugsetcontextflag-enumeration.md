---
title: "CorDebugSetContextFlag Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugSetContextFlag
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugSetContextFlag
helpviewer_keywords: CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 958ed303fab3dcb01fad2040dd06381e76fe5a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="ca384-102">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ca384-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="ca384-103">Bağlam etkin olup olmadığını gösterir (veya yaprak) çerçeve yığında veya başka bir çerçevesinden geriye doğru izleme tarafından hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="ca384-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca384-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca384-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="ca384-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ca384-105">Members</span></span>  
  
|<span data-ttu-id="ca384-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ca384-106">Member</span></span>|<span data-ttu-id="ca384-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca384-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ca384-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="ca384-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="ca384-109">Bağlam iş parçacığının etkin bağlamdır.</span><span class="sxs-lookup"><span data-stu-id="ca384-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="ca384-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="ca384-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="ca384-111">Başka bir çerçevesinden geriye doğru izleme bağlamı hesaplandığı.</span><span class="sxs-lookup"><span data-stu-id="ca384-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca384-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca384-112">Remarks</span></span>  
 <span data-ttu-id="ca384-113">`CorDebugSetContextFlag`tarafından kullanılan değerleri sağlayan [Icordebugstackwalk::setcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ca384-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca384-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca384-114">Requirements</span></span>  
 <span data-ttu-id="ca384-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca384-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca384-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca384-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca384-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca384-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca384-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca384-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca384-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca384-119">See Also</span></span>  
 [<span data-ttu-id="ca384-120">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ca384-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="ca384-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ca384-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
