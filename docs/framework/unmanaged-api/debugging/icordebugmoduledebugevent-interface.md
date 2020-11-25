---
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: 62d419a193cff000e1dd748d0cbb6b61775a81aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695822"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="b346a-102">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b346a-102">ICorDebugModuleDebugEvent Interface</span></span>

<span data-ttu-id="b346a-103">Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b346a-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b346a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b346a-104">Methods</span></span>  
  
|<span data-ttu-id="b346a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b346a-105">Method</span></span>|<span data-ttu-id="b346a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b346a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b346a-107">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b346a-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="b346a-108">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="b346a-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b346a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b346a-109">Remarks</span></span>  

 <span data-ttu-id="b346a-110">[MODULE_LOADED](cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="b346a-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b346a-111">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b346a-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="b346a-112">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="b346a-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b346a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b346a-113">Requirements</span></span>  

 <span data-ttu-id="b346a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b346a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b346a-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b346a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b346a-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b346a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b346a-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b346a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b346a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b346a-118">See also</span></span>

- [<span data-ttu-id="b346a-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b346a-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b346a-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b346a-120">Debugging</span></span>](index.md)
