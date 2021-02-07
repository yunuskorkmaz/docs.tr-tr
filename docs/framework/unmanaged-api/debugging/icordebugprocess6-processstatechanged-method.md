---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugProcess6::P rocessStateChanged yöntemi'
title: ICorDebugProcess6::ProcessStateChanged Yöntemi
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 8060c29598adf5d4bbe7bffb4cd6611ee19a2669
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691373"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="bc46a-103">ICorDebugProcess6::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc46a-103">ICorDebugProcess6::ProcessStateChanged Method</span></span>

<span data-ttu-id="bc46a-104">İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="bc46a-104">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc46a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc46a-105">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc46a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc46a-106">Parameters</span></span>  

 `change`  
 <span data-ttu-id="bc46a-107">'ndaki [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) numaralandırması üyesi</span><span class="sxs-lookup"><span data-stu-id="bc46a-107">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc46a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc46a-108">Remarks</span></span>  

 <span data-ttu-id="bc46a-109">Hata ayıklayıcı, işlemin çalıştığını [ICorDebug](icordebug-interface.md) 'a bildirmek için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="bc46a-109">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc46a-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc46a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc46a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc46a-111">Requirements</span></span>  

 <span data-ttu-id="bc46a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc46a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc46a-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc46a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc46a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bc46a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc46a-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc46a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc46a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc46a-116">See also</span></span>

- [<span data-ttu-id="bc46a-117">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc46a-117">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="bc46a-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bc46a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
