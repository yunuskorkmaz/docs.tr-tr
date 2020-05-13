---
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: ec6bad730d807b9a36ce5bba1c6f5d80da375f6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213339"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="97246-102">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97246-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="97246-103">Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="97246-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97246-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="97246-104">Methods</span></span>  
  
|<span data-ttu-id="97246-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="97246-105">Method</span></span>|<span data-ttu-id="97246-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97246-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97246-107">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97246-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="97246-108">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="97246-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97246-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97246-109">Remarks</span></span>  
 <span data-ttu-id="97246-110">[MODULE_LOADED](cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="97246-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97246-111">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97246-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="97246-112">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="97246-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97246-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97246-113">Requirements</span></span>  
 <span data-ttu-id="97246-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97246-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97246-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97246-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97246-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="97246-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97246-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97246-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97246-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97246-118">See also</span></span>

- [<span data-ttu-id="97246-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="97246-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="97246-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="97246-120">Debugging</span></span>](index.md)
