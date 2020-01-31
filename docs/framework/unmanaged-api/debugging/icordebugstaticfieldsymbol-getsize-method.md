---
title: 'ICorDebugStaticFieldSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: deeb887dad38417e3ebb980f5ef2f89392388d65
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791816"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="f5209-102">ICorDebugStaticFieldSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5209-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="f5209-103">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="f5209-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5209-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5209-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5209-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5209-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="f5209-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f5209-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5209-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5209-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5209-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5209-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5209-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5209-109">Requirements</span></span>  
 <span data-ttu-id="f5209-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5209-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5209-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5209-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5209-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5209-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5209-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5209-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5209-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5209-114">See also</span></span>

- [<span data-ttu-id="f5209-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5209-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f5209-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f5209-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
