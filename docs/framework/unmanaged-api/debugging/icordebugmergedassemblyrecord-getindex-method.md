---
title: ICorDebugMergedAssemblyRecord::GetIndex yöntemi
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0bcb5cdb4e93ae8ce6981bd86f125ecccb7d732
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414843"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="f4346-102">ICorDebugMergedAssemblyRecord::GetIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4346-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="f4346-103">Derlemenin ön eki dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f4346-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4346-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4346-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4346-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4346-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="f4346-106">[out] Önek dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f4346-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4346-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4346-107">Remarks</span></span>  
 <span data-ttu-id="f4346-108">Önek dizin birleştirilmiş meta verileri tür adları ad çakışmaları önlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4346-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4346-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4346-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4346-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4346-110">Requirements</span></span>  
 <span data-ttu-id="f4346-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4346-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4346-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4346-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4346-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4346-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4346-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4346-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4346-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4346-115">See Also</span></span>  
 [<span data-ttu-id="f4346-116">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4346-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="f4346-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f4346-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
