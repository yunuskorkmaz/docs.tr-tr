---
title: 'ICorDebugStaticFieldSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: e36c94bf411e75f915cca86aee74cdf161674d25
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379408"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="92df2-102">ICorDebugStaticFieldSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="92df2-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="92df2-103">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="92df2-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92df2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92df2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92df2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92df2-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="92df2-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="92df2-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92df2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92df2-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92df2-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="92df2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92df2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92df2-109">Requirements</span></span>  
 <span data-ttu-id="92df2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92df2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92df2-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92df2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92df2-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92df2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92df2-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92df2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92df2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92df2-114">See also</span></span>

- [<span data-ttu-id="92df2-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92df2-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="92df2-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="92df2-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
