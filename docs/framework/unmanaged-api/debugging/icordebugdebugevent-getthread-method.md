---
title: ICorDebugDebugEvent::GetThread Metodu
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51d674159b33cad1a77a82e39b9f11a38c98cbd3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687407"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="6c0f5-102">ICorDebugDebugEvent::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="6c0f5-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="6c0f5-103">Olayın gerçekleştiği iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c0f5-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c0f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c0f5-105">Parameters</span></span>  
 <span data-ttu-id="6c0f5-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="6c0f5-106">ppThread</span></span>  
 <span data-ttu-id="6c0f5-107">[out] Olayın gerçekleştiği iş parçacığını temsil eden bir Icordebugthread nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c0f5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c0f5-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c0f5-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c0f5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c0f5-110">Requirements</span></span>  
 <span data-ttu-id="6c0f5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c0f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0f5-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c0f5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c0f5-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c0f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c0f5-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c0f5-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0f5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-115">See also</span></span>
- [<span data-ttu-id="6c0f5-116">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c0f5-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="6c0f5-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c0f5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
