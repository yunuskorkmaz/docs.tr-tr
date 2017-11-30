---
title: ICorDebugModuleDebugEvent arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dced93ab39529ec57fb6fb99603a197fb957be8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="25eae-102">ICorDebugModuleDebugEvent arabirimi</span><span class="sxs-lookup"><span data-stu-id="25eae-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="25eae-103">Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) modül düzeyi olaylarını desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="25eae-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25eae-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="25eae-104">Methods</span></span>  
  
|<span data-ttu-id="25eae-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="25eae-105">Method</span></span>|<span data-ttu-id="25eae-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25eae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25eae-107">GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="25eae-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="25eae-108">Yalnızca yüklü veya kaldırılmış birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="25eae-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25eae-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25eae-109">Remarks</span></span>  
 <span data-ttu-id="25eae-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türleri bu arabirim uygulama.</span><span class="sxs-lookup"><span data-stu-id="25eae-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25eae-111">Arabirimi yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25eae-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="25eae-112">Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="25eae-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25eae-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25eae-113">Requirements</span></span>  
 <span data-ttu-id="25eae-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25eae-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25eae-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25eae-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25eae-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25eae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25eae-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25eae-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25eae-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25eae-118">See Also</span></span>  
 [<span data-ttu-id="25eae-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="25eae-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="25eae-120">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="25eae-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
