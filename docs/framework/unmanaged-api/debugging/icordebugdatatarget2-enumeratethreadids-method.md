---
title: ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 594fcb74988cadaa4801fc6f0bb2d05b27a7f441
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563398"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="51c92-102">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51c92-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="51c92-103">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="51c92-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51c92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51c92-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51c92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51c92-105">Parameters</span></span>  
 <span data-ttu-id="51c92-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="51c92-106">cThreadIDs</span></span>  
 <span data-ttu-id="51c92-107">[in] Kimlikleri döndürülen iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="51c92-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="51c92-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="51c92-108">pcThreadIds</span></span>  
 <span data-ttu-id="51c92-109">[out] Bir işaretçi bir `ULONG32` iş parçacığı kimlikleri yazılan gerçek sayısını gösteren `pThreadIds` dizisi.</span><span class="sxs-lookup"><span data-stu-id="51c92-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="51c92-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="51c92-110">pThreadIDs</span></span>  
 <span data-ttu-id="51c92-111">İş parçacığı tanımlayıcılarının dizisi.</span><span class="sxs-lookup"><span data-stu-id="51c92-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51c92-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51c92-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51c92-113">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51c92-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51c92-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51c92-114">Requirements</span></span>  
 <span data-ttu-id="51c92-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md). **Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51c92-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51c92-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51c92-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51c92-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51c92-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c92-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51c92-118">See also</span></span>
- [<span data-ttu-id="51c92-119">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51c92-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="51c92-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="51c92-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
