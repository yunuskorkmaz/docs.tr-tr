---
title: "ICorDebugProcess6::ProcessStateChanged Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 22fe068af577c3c3eb056acae388747f88d3f8df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="5d7c0-102">ICorDebugProcess6::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d7c0-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="5d7c0-103">Bildirir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) işlemin çalıştığı.</span><span class="sxs-lookup"><span data-stu-id="5d7c0-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d7c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d7c0-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d7c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d7c0-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="5d7c0-106">[in] Üye [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5d7c0-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d7c0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d7c0-107">Remarks</span></span>  
 <span data-ttu-id="5d7c0-108">Hata ayıklayıcı bildirmek için bu yöntemi çağırır [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) işlemin çalıştığı.</span><span class="sxs-lookup"><span data-stu-id="5d7c0-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d7c0-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d7c0-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d7c0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d7c0-110">Requirements</span></span>  
 <span data-ttu-id="5d7c0-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d7c0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d7c0-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d7c0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d7c0-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d7c0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d7c0-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d7c0-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7c0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d7c0-115">See Also</span></span>  
 [<span data-ttu-id="5d7c0-116">Icordebugprocess6 arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d7c0-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="5d7c0-117">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d7c0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
