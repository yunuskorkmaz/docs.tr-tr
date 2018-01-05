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
ms.workload: dotnet
ms.openlocfilehash: 9e5aad3e95668525fe607bf4e90b4e05b2b58cad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="1815a-102">ICorDebugProcess6::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1815a-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="1815a-103">Bildirir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) işlemin çalıştığı.</span><span class="sxs-lookup"><span data-stu-id="1815a-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1815a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1815a-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1815a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1815a-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="1815a-106">[in] Üye [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1815a-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1815a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1815a-107">Remarks</span></span>  
 <span data-ttu-id="1815a-108">Hata ayıklayıcı bildirmek için bu yöntemi çağırır [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) işlemin çalıştığı.</span><span class="sxs-lookup"><span data-stu-id="1815a-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1815a-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1815a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1815a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1815a-110">Requirements</span></span>  
 <span data-ttu-id="1815a-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1815a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1815a-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1815a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1815a-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1815a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1815a-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1815a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1815a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1815a-115">See Also</span></span>  
 [<span data-ttu-id="1815a-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1815a-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="1815a-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1815a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
