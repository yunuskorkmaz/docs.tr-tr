---
title: ICorDebugInstanceFieldSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0901e64a7da7f68b2fbcdb63636503893263435f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413796"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="3828f-102">ICorDebugInstanceFieldSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="3828f-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="3828f-103">Örnek alanı bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="3828f-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3828f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3828f-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3828f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3828f-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="3828f-106">[out] Alanın uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3828f-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3828f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3828f-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3828f-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3828f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3828f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3828f-109">Requirements</span></span>  
 <span data-ttu-id="3828f-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3828f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3828f-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3828f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3828f-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3828f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3828f-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3828f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3828f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3828f-114">See Also</span></span>  
 [<span data-ttu-id="3828f-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3828f-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="3828f-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3828f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
