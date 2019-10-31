---
title: ICorDebugILCode2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 9c1a5cde5a39a334d655d865c5e44a5eb0c1766a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131038"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="15128-102">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15128-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="15128-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="15128-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="15128-104">Bir işlevin yerel değişken imzasının belirtecini döndüren ve bir profiler 'ın belgelenmiş ara dili (IL) orijinal Yöntem Il uzaklıklarına eşleyen Yöntemler sağlamak için [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="15128-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15128-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="15128-105">Methods</span></span>  
  
|<span data-ttu-id="15128-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="15128-106">Method</span></span>|<span data-ttu-id="15128-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15128-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15128-108">GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15128-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="15128-109">Bu örnek için, Oluşturucu tarafından işaretlenmiş Il uzaklıkları orijinal Yöntem Il uzaklıklarından bir harita döndürür.</span><span class="sxs-lookup"><span data-stu-id="15128-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="15128-110">GetLocalVarSigToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15128-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="15128-111">Bu örnek tarafından temsil edilen işlev için yerel değişken imzasının meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="15128-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15128-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15128-112">Requirements</span></span>  
 <span data-ttu-id="15128-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15128-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15128-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="15128-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15128-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="15128-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15128-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15128-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15128-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15128-117">See also</span></span>

- [<span data-ttu-id="15128-118">ICorDebugILCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15128-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="15128-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15128-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="15128-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="15128-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
