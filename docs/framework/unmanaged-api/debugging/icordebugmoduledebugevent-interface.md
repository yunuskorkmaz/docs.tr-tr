---
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bf1fa21872c710ebc69c45e9980aeaa577a45fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160920"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="f666d-102">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f666d-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="f666d-103">Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) Modül düzeyinde olaylar desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="f666d-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f666d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f666d-104">Methods</span></span>  
  
|<span data-ttu-id="f666d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f666d-105">Method</span></span>|<span data-ttu-id="f666d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f666d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f666d-107">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f666d-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="f666d-108">Yalnızca yüklü veya kaldırılmış birleştirilmiş modül alır.</span><span class="sxs-lookup"><span data-stu-id="f666d-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f666d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f666d-109">Remarks</span></span>  
 <span data-ttu-id="f666d-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f666d-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f666d-111">Arabirimi yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f666d-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="f666d-112">Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.</span><span class="sxs-lookup"><span data-stu-id="f666d-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f666d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f666d-113">Requirements</span></span>  
 <span data-ttu-id="f666d-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f666d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f666d-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f666d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f666d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f666d-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f666d-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f666d-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f666d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f666d-118">See also</span></span>

- [<span data-ttu-id="f666d-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f666d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f666d-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f666d-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
