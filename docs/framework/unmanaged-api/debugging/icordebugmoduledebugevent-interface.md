---
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: cca181c6af6db9f35ff7913e045a30e37e07a5e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110245"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="86cdd-102">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86cdd-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="86cdd-103">Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="86cdd-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86cdd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="86cdd-104">Methods</span></span>  
  
|<span data-ttu-id="86cdd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="86cdd-105">Method</span></span>|<span data-ttu-id="86cdd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86cdd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86cdd-107">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86cdd-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="86cdd-108">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="86cdd-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86cdd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86cdd-109">Remarks</span></span>  
 <span data-ttu-id="86cdd-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="86cdd-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86cdd-111">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86cdd-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="86cdd-112">Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.</span><span class="sxs-lookup"><span data-stu-id="86cdd-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86cdd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86cdd-113">Requirements</span></span>  
 <span data-ttu-id="86cdd-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86cdd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86cdd-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86cdd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86cdd-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86cdd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86cdd-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86cdd-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86cdd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86cdd-118">See also</span></span>

- [<span data-ttu-id="86cdd-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86cdd-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="86cdd-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="86cdd-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
