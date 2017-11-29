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
ms.openlocfilehash: dac64c785077fc3901e712498e66e11b9c9f3279
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="463b4-102">ICorDebugMergedAssemblyRecord::GetIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="463b4-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="463b4-103">Derlemenin ön eki dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="463b4-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="463b4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="463b4-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="463b4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="463b4-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="463b4-106">[out] Önek dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="463b4-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="463b4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="463b4-107">Remarks</span></span>  
 <span data-ttu-id="463b4-108">Önek dizin birleştirilmiş meta verileri tür adları ad çakışmaları önlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="463b4-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="463b4-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="463b4-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="463b4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="463b4-110">Requirements</span></span>  
 <span data-ttu-id="463b4-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="463b4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="463b4-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="463b4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="463b4-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="463b4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="463b4-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="463b4-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463b4-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="463b4-115">See Also</span></span>  
 [<span data-ttu-id="463b4-116">ICorDebugMergedAssemblyRecord arabirimi</span><span class="sxs-lookup"><span data-stu-id="463b4-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="463b4-117">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="463b4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
