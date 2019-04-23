---
title: ICorDebugDebugEvent::GetThread Yöntemi
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103768918f67ca695a47c52b9cd97f24fb8d46ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081586"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="664b3-102">ICorDebugDebugEvent::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="664b3-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="664b3-103">Olayın gerçekleştiği iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="664b3-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="664b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="664b3-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="664b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="664b3-105">Parameters</span></span>  
 <span data-ttu-id="664b3-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="664b3-106">ppThread</span></span>  
 <span data-ttu-id="664b3-107">[out] Olayın gerçekleştiği iş parçacığını temsil eden bir Icordebugthread nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="664b3-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="664b3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="664b3-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="664b3-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="664b3-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="664b3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="664b3-110">Requirements</span></span>  
 <span data-ttu-id="664b3-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="664b3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="664b3-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="664b3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="664b3-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="664b3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="664b3-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="664b3-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="664b3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="664b3-115">See also</span></span>

- [<span data-ttu-id="664b3-116">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="664b3-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="664b3-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="664b3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
