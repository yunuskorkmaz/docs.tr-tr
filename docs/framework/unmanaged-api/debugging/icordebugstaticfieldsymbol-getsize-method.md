---
title: 'ICorDebugStaticFieldSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d99e06c1093dbc67e9c1999e4b9ccabd6579340e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962668"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="6dbe9-102">ICorDebugStaticFieldSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="6dbe9-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="6dbe9-103">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="6dbe9-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dbe9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6dbe9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dbe9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6dbe9-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="6dbe9-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6dbe9-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dbe9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6dbe9-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6dbe9-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6dbe9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dbe9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6dbe9-109">Requirements</span></span>  
 <span data-ttu-id="6dbe9-110">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dbe9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dbe9-111">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6dbe9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6dbe9-112">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6dbe9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dbe9-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dbe9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbe9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dbe9-114">See also</span></span>

- [<span data-ttu-id="6dbe9-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6dbe9-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="6dbe9-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6dbe9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
