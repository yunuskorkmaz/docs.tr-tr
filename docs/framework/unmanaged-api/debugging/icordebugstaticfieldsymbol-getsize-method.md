---
title: 'ICorDebugStaticFieldSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: 34567247935588363d96b141717d7ec07bb76546
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677217"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="65092-102">ICorDebugStaticFieldSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="65092-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="65092-103">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="65092-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65092-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="65092-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65092-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65092-105">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="65092-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65092-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65092-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65092-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65092-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="65092-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65092-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65092-109">Requirements</span></span>  

 <span data-ttu-id="65092-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65092-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65092-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65092-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65092-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="65092-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65092-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65092-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65092-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65092-114">See also</span></span>

- [<span data-ttu-id="65092-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65092-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="65092-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="65092-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
