---
title: ICorDebugInstanceFieldSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be2119b1ce43d5969c8d083e955210c69af69b44
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491444"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="73f83-102">ICorDebugInstanceFieldSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="73f83-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="73f83-103">Örnek alanı bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="73f83-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73f83-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73f83-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73f83-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73f83-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="73f83-106">[out] Alanın uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73f83-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73f83-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73f83-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73f83-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73f83-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73f83-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73f83-109">Requirements</span></span>  
 <span data-ttu-id="73f83-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73f83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73f83-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73f83-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73f83-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73f83-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73f83-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73f83-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f83-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73f83-114">See also</span></span>
- [<span data-ttu-id="73f83-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73f83-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="73f83-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="73f83-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
