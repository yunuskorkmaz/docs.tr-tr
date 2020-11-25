---
title: ICorDebugProcess6::ProcessStateChanged Yöntemi
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 006c81e0339a00aac14fb4f83f2bc140990bd546
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732586"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="3b280-102">ICorDebugProcess6::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b280-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>

<span data-ttu-id="3b280-103">İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="3b280-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b280-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3b280-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b280-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b280-105">Parameters</span></span>  

 `change`  
 <span data-ttu-id="3b280-106">'ndaki [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) numaralandırması üyesi</span><span class="sxs-lookup"><span data-stu-id="3b280-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b280-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b280-107">Remarks</span></span>  

 <span data-ttu-id="3b280-108">Hata ayıklayıcı, işlemin çalıştığını [ICorDebug](icordebug-interface.md) 'a bildirmek için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="3b280-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b280-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b280-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b280-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b280-110">Requirements</span></span>  

 <span data-ttu-id="3b280-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b280-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b280-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3b280-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b280-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3b280-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b280-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b280-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b280-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b280-115">See also</span></span>

- [<span data-ttu-id="3b280-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b280-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="3b280-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3b280-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
