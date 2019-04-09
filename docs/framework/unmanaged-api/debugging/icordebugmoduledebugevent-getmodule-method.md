---
title: ICorDebugModuleDebugEvent::GetModule yöntemi
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c0cc1305f47f03c8c9b35bab5c980cb23d1b157
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138443"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="236c7-102">ICorDebugModuleDebugEvent::GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="236c7-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="236c7-103">Yalnızca yüklü veya kaldırılmış birleştirilmiş modül alır.</span><span class="sxs-lookup"><span data-stu-id="236c7-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="236c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="236c7-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="236c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="236c7-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="236c7-106">[out] Yalnızca yüklü veya kaldırılmış birleştirilmiş modülü temsil eden bir Icordebugmodule nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="236c7-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="236c7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="236c7-107">Remarks</span></span>  
 <span data-ttu-id="236c7-108">Çağırabilirsiniz [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) Modülü yüklü veya kaldırılmış olup olmadığını belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="236c7-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="236c7-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="236c7-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236c7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="236c7-110">Requirements</span></span>  
 <span data-ttu-id="236c7-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236c7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236c7-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="236c7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="236c7-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="236c7-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="236c7-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="236c7-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="236c7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="236c7-115">See also</span></span>

- [<span data-ttu-id="236c7-116">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="236c7-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="236c7-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="236c7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
