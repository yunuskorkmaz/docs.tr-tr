---
title: ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70b3b57b51faed51aa7d5a70a3b785e0f719321b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916571"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="2fd9d-102">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fd9d-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="2fd9d-103">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fd9d-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fd9d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fd9d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2fd9d-105">Parameters</span></span>  
 <span data-ttu-id="2fd9d-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="2fd9d-106">cThreadIDs</span></span>  
 <span data-ttu-id="2fd9d-107">[in] Kimlikleri döndürülen iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="2fd9d-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="2fd9d-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="2fd9d-108">pcThreadIds</span></span>  
 <span data-ttu-id="2fd9d-109">[out] Bir işaretçi bir `ULONG32` iş parçacığı kimlikleri yazılan gerçek sayısını gösteren `pThreadIds` dizisi.</span><span class="sxs-lookup"><span data-stu-id="2fd9d-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="2fd9d-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="2fd9d-110">pThreadIDs</span></span>  
 <span data-ttu-id="2fd9d-111">İş parçacığı tanımlayıcılarının dizisi.</span><span class="sxs-lookup"><span data-stu-id="2fd9d-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fd9d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fd9d-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fd9d-113">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2fd9d-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fd9d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fd9d-114">Requirements</span></span>  
 <span data-ttu-id="2fd9d-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md). **Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fd9d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fd9d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fd9d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fd9d-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd9d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd9d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fd9d-118">See also</span></span>

- [<span data-ttu-id="2fd9d-119">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fd9d-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="2fd9d-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2fd9d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
