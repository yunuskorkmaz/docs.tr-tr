---
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: a2c7eaa8a2c811c1696024d9af4b715cc49e7caa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792890"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="86e24-102">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86e24-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="86e24-103">Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="86e24-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86e24-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="86e24-104">Methods</span></span>  
  
|<span data-ttu-id="86e24-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="86e24-105">Method</span></span>|<span data-ttu-id="86e24-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86e24-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86e24-107">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86e24-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="86e24-108">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="86e24-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e24-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86e24-109">Remarks</span></span>  
 <span data-ttu-id="86e24-110">[MODULE_LOADED](cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="86e24-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86e24-111">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86e24-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="86e24-112">Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.</span><span class="sxs-lookup"><span data-stu-id="86e24-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e24-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86e24-113">Requirements</span></span>  
 <span data-ttu-id="86e24-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86e24-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e24-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86e24-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86e24-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86e24-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86e24-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e24-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e24-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86e24-118">See also</span></span>

- [<span data-ttu-id="86e24-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86e24-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="86e24-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="86e24-120">Debugging</span></span>](index.md)
