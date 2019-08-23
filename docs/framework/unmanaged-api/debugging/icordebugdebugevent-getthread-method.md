---
title: ICorDebugDebugEvent::GetThread Yöntemi
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f85dccd5b59610c52adcf685828984c9344fd49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911277"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="e98e1-102">ICorDebugDebugEvent::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e98e1-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="e98e1-103">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="e98e1-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e98e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e98e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e98e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e98e1-105">Parameters</span></span>  
 <span data-ttu-id="e98e1-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="e98e1-106">ppThread</span></span>  
 <span data-ttu-id="e98e1-107">dışı Olayın gerçekleştiği iş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e98e1-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e98e1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e98e1-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e98e1-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e98e1-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e98e1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e98e1-110">Requirements</span></span>  
 <span data-ttu-id="e98e1-111">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e98e1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e98e1-112">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e98e1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e98e1-113">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e98e1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e98e1-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e98e1-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e98e1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e98e1-115">See also</span></span>

- [<span data-ttu-id="e98e1-116">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e98e1-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="e98e1-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e98e1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
