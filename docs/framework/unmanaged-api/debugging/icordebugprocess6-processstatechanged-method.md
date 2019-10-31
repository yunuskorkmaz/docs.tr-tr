---
title: ICorDebugProcess6::ProcessStateChanged Yöntemi
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 3927e57883ebe282b262cb03ececc3b2cd96fd46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123422"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="aeee3-102">ICorDebugProcess6::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeee3-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="aeee3-103">İşlemin çalıştığını [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="aeee3-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeee3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aeee3-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeee3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aeee3-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="aeee3-106">'ndaki [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) numaralandırması üyesi</span><span class="sxs-lookup"><span data-stu-id="aeee3-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeee3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeee3-107">Remarks</span></span>  
 <span data-ttu-id="aeee3-108">Hata ayıklayıcı, işlemin çalıştığını [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) 'a bildirmek için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="aeee3-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aeee3-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeee3-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeee3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeee3-110">Requirements</span></span>  
 <span data-ttu-id="aeee3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeee3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeee3-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aeee3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeee3-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aeee3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeee3-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeee3-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeee3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeee3-115">See also</span></span>

- [<span data-ttu-id="aeee3-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeee3-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="aeee3-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aeee3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
