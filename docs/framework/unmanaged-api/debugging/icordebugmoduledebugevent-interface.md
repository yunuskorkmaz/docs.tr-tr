---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugmoduledebugger gevent arabirimi'
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: 0c2d43d7b04caeea0407ede23f0df6e278d60c92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801039"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="16679-103">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16679-103">ICorDebugModuleDebugEvent Interface</span></span>

<span data-ttu-id="16679-104">Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="16679-104">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16679-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="16679-105">Methods</span></span>  
  
|<span data-ttu-id="16679-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="16679-106">Method</span></span>|<span data-ttu-id="16679-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16679-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16679-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16679-108">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="16679-109">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="16679-109">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16679-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16679-110">Remarks</span></span>  

 <span data-ttu-id="16679-111">[MODULE_LOADED](cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="16679-111">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16679-112">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16679-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="16679-113">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="16679-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16679-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16679-114">Requirements</span></span>  

 <span data-ttu-id="16679-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16679-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16679-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16679-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16679-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16679-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16679-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16679-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16679-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16679-119">See also</span></span>

- [<span data-ttu-id="16679-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="16679-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="16679-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="16679-121">Debugging</span></span>](index.md)
