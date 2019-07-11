---
title: ICorDebugStaticFieldSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a30778a287b4115df552444549a92c006288005
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760759"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="4e54d-102">ICorDebugStaticFieldSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e54d-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="4e54d-103">Boyutu bayt cinsinden statik alanı alır.</span><span class="sxs-lookup"><span data-stu-id="4e54d-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e54d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e54d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e54d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e54d-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="4e54d-106">[out] Alanın uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e54d-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e54d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e54d-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e54d-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e54d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e54d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e54d-109">Requirements</span></span>  
 <span data-ttu-id="4e54d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e54d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e54d-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e54d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e54d-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e54d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e54d-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e54d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e54d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e54d-114">See also</span></span>

- [<span data-ttu-id="4e54d-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e54d-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="4e54d-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e54d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
