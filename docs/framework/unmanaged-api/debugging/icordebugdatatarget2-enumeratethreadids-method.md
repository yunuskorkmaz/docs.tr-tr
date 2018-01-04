---
title: "ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9030f7f8453de98f535cf8212e55c7daee94e8e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="9e860-102">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e860-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="9e860-103">Etkin iş parçacığı kimlikleri listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e860-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e860-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e860-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e860-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e860-105">Parameters</span></span>  
 <span data-ttu-id="9e860-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="9e860-106">cThreadIDs</span></span>  
 <span data-ttu-id="9e860-107">[in] İş parçacığı, kimlikleri döndürülebilecek maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="9e860-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="9e860-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="9e860-108">pcThreadIds</span></span>  
 <span data-ttu-id="9e860-109">[out] Bir işaretçi bir `ULONG32` iş parçacığı kimlikleri yazılan gerçek sayısını gösterir `pThreadIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="9e860-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="9e860-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="9e860-110">pThreadIDs</span></span>  
 <span data-ttu-id="9e860-111">İş parçacığı tanımlayıcıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="9e860-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e860-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e860-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e860-113">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e860-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e860-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e860-114">Requirements</span></span>  
 <span data-ttu-id="9e860-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md). **Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e860-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e860-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e860-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e860-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e860-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e860-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e860-118">See Also</span></span>  
 [<span data-ttu-id="9e860-119">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e860-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="9e860-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e860-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
