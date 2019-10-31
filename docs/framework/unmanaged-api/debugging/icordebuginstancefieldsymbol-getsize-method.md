---
title: 'Icordebugınstancefieldsymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 71828cd8486e2ff09190d23473dbab303b92f933
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139026"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="5ada7-102">Icordebugınstancefieldsymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ada7-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="5ada7-103">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5ada7-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ada7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ada7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ada7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ada7-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="5ada7-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ada7-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ada7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ada7-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ada7-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ada7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ada7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ada7-109">Requirements</span></span>  
 <span data-ttu-id="5ada7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ada7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ada7-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5ada7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ada7-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5ada7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ada7-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ada7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ada7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ada7-114">See also</span></span>

- [<span data-ttu-id="5ada7-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ada7-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="5ada7-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5ada7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
