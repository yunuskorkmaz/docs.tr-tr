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
ms.openlocfilehash: c20b7dd1bcbc27edb9be11419b7919250301d488
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="3f7d7-102">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f7d7-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="3f7d7-103">Etkin iş parçacığı kimlikleri listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f7d7-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f7d7-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f7d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f7d7-105">Parameters</span></span>  
 <span data-ttu-id="3f7d7-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="3f7d7-106">cThreadIDs</span></span>  
 <span data-ttu-id="3f7d7-107">[in] İş parçacığı, kimlikleri döndürülebilecek maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="3f7d7-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="3f7d7-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="3f7d7-108">pcThreadIds</span></span>  
 <span data-ttu-id="3f7d7-109">[out] Bir işaretçi bir `ULONG32` iş parçacığı kimlikleri yazılan gerçek sayısını gösterir `pThreadIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="3f7d7-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="3f7d7-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="3f7d7-110">pThreadIDs</span></span>  
 <span data-ttu-id="3f7d7-111">İş parçacığı tanımlayıcıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="3f7d7-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f7d7-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f7d7-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f7d7-113">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f7d7-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7d7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f7d7-114">Requirements</span></span>  
 <span data-ttu-id="3f7d7-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md). **Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f7d7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f7d7-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f7d7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f7d7-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f7d7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7d7-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f7d7-118">See Also</span></span>  
 [<span data-ttu-id="3f7d7-119">Icordebugdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f7d7-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="3f7d7-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3f7d7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
