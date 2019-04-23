---
title: ICorDebugMergedAssemblyRecord::GetIndex yöntemi
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8ba470325098125aee8ef7de01fa6aa70596d42
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202605"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="6f242-102">ICorDebugMergedAssemblyRecord::GetIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f242-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="6f242-103">Derlemenin ön eki dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="6f242-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f242-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f242-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f242-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f242-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="6f242-106">[out] Önek dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f242-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f242-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f242-107">Remarks</span></span>  
 <span data-ttu-id="6f242-108">Ön ek dizin birleştirilmiş meta tür adları ad çakışmalarını önlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f242-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f242-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f242-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f242-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f242-110">Requirements</span></span>  
 <span data-ttu-id="6f242-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f242-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f242-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f242-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f242-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f242-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f242-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f242-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f242-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f242-115">See also</span></span>

- [<span data-ttu-id="6f242-116">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f242-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="6f242-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6f242-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
