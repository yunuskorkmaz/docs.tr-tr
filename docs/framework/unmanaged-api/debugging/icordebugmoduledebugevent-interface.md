---
title: ICorDebugModuleDebugEvent arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f35c26b98521311267a627265f2dae8fa9e333de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421846"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="a3adc-102">ICorDebugModuleDebugEvent arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3adc-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="a3adc-103">Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) modül düzeyi olaylarını desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="a3adc-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3adc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a3adc-104">Methods</span></span>  
  
|<span data-ttu-id="a3adc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a3adc-105">Method</span></span>|<span data-ttu-id="a3adc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3adc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3adc-107">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3adc-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="a3adc-108">Yalnızca yüklü veya kaldırılmış birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="a3adc-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3adc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3adc-109">Remarks</span></span>  
 <span data-ttu-id="a3adc-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türleri bu arabirim uygulama.</span><span class="sxs-lookup"><span data-stu-id="a3adc-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3adc-111">Arabirimi yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3adc-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="a3adc-112">Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="a3adc-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3adc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3adc-113">Requirements</span></span>  
 <span data-ttu-id="a3adc-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3adc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3adc-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3adc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3adc-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3adc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3adc-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3adc-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3adc-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3adc-118">See Also</span></span>  
 [<span data-ttu-id="a3adc-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a3adc-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a3adc-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a3adc-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
