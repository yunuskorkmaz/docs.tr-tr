---
title: ICorDebugProcess6::ProcessStateChanged Yöntemi
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792211"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="159d2-102">ICorDebugProcess6::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="159d2-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="159d2-103">İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="159d2-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="159d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="159d2-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="159d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="159d2-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="159d2-106">'ndaki [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) numaralandırması üyesi</span><span class="sxs-lookup"><span data-stu-id="159d2-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="159d2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="159d2-107">Remarks</span></span>  
 <span data-ttu-id="159d2-108">Hata ayıklayıcı, işlemin çalıştığını [ICorDebug](icordebug-interface.md) 'a bildirmek için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="159d2-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="159d2-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="159d2-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="159d2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="159d2-110">Requirements</span></span>  
 <span data-ttu-id="159d2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="159d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="159d2-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="159d2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="159d2-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="159d2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="159d2-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="159d2-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="159d2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="159d2-115">See also</span></span>

- [<span data-ttu-id="159d2-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="159d2-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="159d2-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="159d2-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
