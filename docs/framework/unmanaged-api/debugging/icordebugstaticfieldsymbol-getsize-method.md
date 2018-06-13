---
title: ICorDebugStaticFieldSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acb72a7d6c39efa5fa93bfddc314d07ec6cd8348
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419100"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="b69aa-102">ICorDebugStaticFieldSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="b69aa-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="b69aa-103">Statik alanının bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="b69aa-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b69aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b69aa-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b69aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b69aa-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="b69aa-106">[out] Alanın uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b69aa-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b69aa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b69aa-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b69aa-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b69aa-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b69aa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b69aa-109">Requirements</span></span>  
 <span data-ttu-id="b69aa-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b69aa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b69aa-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b69aa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b69aa-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b69aa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b69aa-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b69aa-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b69aa-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b69aa-114">See Also</span></span>  
 [<span data-ttu-id="b69aa-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b69aa-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="b69aa-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b69aa-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
