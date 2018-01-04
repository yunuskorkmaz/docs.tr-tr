---
title: "ICorDebugMergedAssemblyRecord::GetIndex yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54ff8d6935f5507ab02d9d566921cb7f8a890bb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="32b85-102">ICorDebugMergedAssemblyRecord::GetIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="32b85-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="32b85-103">Derlemenin ön eki dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="32b85-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32b85-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32b85-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32b85-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32b85-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="32b85-106">[out] Önek dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="32b85-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32b85-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32b85-107">Remarks</span></span>  
 <span data-ttu-id="32b85-108">Önek dizin birleştirilmiş meta verileri tür adları ad çakışmaları önlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32b85-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32b85-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="32b85-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32b85-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32b85-110">Requirements</span></span>  
 <span data-ttu-id="32b85-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32b85-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32b85-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32b85-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32b85-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32b85-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32b85-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32b85-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b85-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32b85-115">See Also</span></span>  
 [<span data-ttu-id="32b85-116">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32b85-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="32b85-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="32b85-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
