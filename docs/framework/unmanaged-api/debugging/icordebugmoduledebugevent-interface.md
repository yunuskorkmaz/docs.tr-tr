---
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 706f392652c5cb868e09d4ee9fcb69c6d3d92d2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965093"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="0b59c-102">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b59c-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="0b59c-103">Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="0b59c-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b59c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b59c-104">Methods</span></span>  
  
|<span data-ttu-id="0b59c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0b59c-105">Method</span></span>|<span data-ttu-id="0b59c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b59c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b59c-107">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b59c-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="0b59c-108">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="0b59c-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b59c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b59c-109">Remarks</span></span>  
 <span data-ttu-id="0b59c-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="0b59c-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b59c-111">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b59c-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="0b59c-112">.NET Native dışında ICorDebug senaryolarına `QueryInterface` `E_NOINTERFACE` yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="0b59c-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b59c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b59c-113">Requirements</span></span>  
 <span data-ttu-id="0b59c-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b59c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b59c-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b59c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b59c-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b59c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b59c-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b59c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b59c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b59c-118">See also</span></span>

- [<span data-ttu-id="0b59c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b59c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0b59c-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0b59c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
