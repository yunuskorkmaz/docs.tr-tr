---
title: "ICorDebugModuleDebugEvent::GetModule yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b11ab8991a9f44cf2868474a8a0f6dcc1c3308c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="3692c-102">ICorDebugModuleDebugEvent::GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="3692c-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="3692c-103">Yalnızca yüklü veya kaldırılmış birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="3692c-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3692c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3692c-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3692c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3692c-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="3692c-106">[out] Bir işaretçi adresine Icordebugmodule nesnenin yalnızca yüklenen veya kaldırıldığında birleştirilmiş modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3692c-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3692c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3692c-107">Remarks</span></span>  
 <span data-ttu-id="3692c-108">Çağırabilirsiniz [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) Modülü yüklü veya kaldırıldığında olup olmadığını belirlemek amacıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3692c-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3692c-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3692c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3692c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3692c-110">Requirements</span></span>  
 <span data-ttu-id="3692c-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3692c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3692c-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3692c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3692c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3692c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3692c-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3692c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3692c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3692c-115">See Also</span></span>  
 [<span data-ttu-id="3692c-116">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3692c-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [<span data-ttu-id="3692c-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3692c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
