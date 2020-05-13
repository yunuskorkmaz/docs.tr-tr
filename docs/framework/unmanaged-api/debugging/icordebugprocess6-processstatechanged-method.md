---
title: ICorDebugProcess6::ProcessStateChanged Yöntemi
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 6be216741e902b15efc3a3ece95cb4a4229960e3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212860"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="0419e-102">ICorDebugProcess6::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0419e-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="0419e-103">İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="0419e-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0419e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0419e-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0419e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0419e-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="0419e-106">'ndaki [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) numaralandırması üyesi</span><span class="sxs-lookup"><span data-stu-id="0419e-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0419e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0419e-107">Remarks</span></span>  
 <span data-ttu-id="0419e-108">Hata ayıklayıcı, işlemin çalıştığını [ICorDebug](icordebug-interface.md) 'a bildirmek için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0419e-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0419e-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0419e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0419e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0419e-110">Requirements</span></span>  
 <span data-ttu-id="0419e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0419e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0419e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0419e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0419e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0419e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0419e-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0419e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0419e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0419e-115">See also</span></span>

- [<span data-ttu-id="0419e-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0419e-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="0419e-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0419e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
