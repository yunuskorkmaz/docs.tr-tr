---
title: ICorDebugStaticFieldSymbol::GetAddress yöntemi
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a78df94fdc4190a43c80b0a8e3457f164e38eb00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498061"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="1652d-102">ICorDebugStaticFieldSymbol::GetAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="1652d-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="1652d-103">Statik alan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="1652d-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1652d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1652d-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1652d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1652d-105">Parameters</span></span>  
 <span data-ttu-id="1652d-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="1652d-106">pRVA</span></span>  
 <span data-ttu-id="1652d-107">[out] Statik alan göreli sanal adres (RVA) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1652d-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1652d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1652d-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1652d-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1652d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1652d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1652d-110">Requirements</span></span>  
 <span data-ttu-id="1652d-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1652d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1652d-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1652d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1652d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1652d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1652d-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1652d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1652d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1652d-115">See also</span></span>
- [<span data-ttu-id="1652d-116">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1652d-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="1652d-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1652d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
