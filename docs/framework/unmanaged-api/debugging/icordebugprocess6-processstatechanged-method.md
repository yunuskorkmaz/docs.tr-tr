---
title: ICorDebugProcess6::ProcessStateChanged Yöntemi
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4dcee3b396d9533f3169db1ea54a6cdc6086c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948596"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="94076-102">ICorDebugProcess6::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94076-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="94076-103">Bildirir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , işlem çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="94076-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94076-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94076-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94076-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94076-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="94076-106">[in] Üye [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) numaralandırması</span><span class="sxs-lookup"><span data-stu-id="94076-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94076-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94076-107">Remarks</span></span>  
 <span data-ttu-id="94076-108">Hata ayıklayıcı bildirmek için bu yöntemi çağırır [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , işlem çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="94076-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94076-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94076-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94076-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94076-110">Requirements</span></span>  
 <span data-ttu-id="94076-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94076-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94076-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94076-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94076-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94076-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94076-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94076-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94076-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94076-115">See also</span></span>

- [<span data-ttu-id="94076-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94076-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="94076-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94076-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
