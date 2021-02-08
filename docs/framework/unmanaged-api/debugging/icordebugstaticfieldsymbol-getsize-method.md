---
description: ': ICorDebugStaticFieldSymbol:: GetSize yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugStaticFieldSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: f6fd2fe60d7cb8a77dcff5ca259d05ae1ef195ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794695"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="c5c17-103">ICorDebugStaticFieldSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5c17-103">ICorDebugStaticFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="c5c17-104">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c5c17-104">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c17-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5c17-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5c17-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5c17-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="c5c17-107">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5c17-107">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5c17-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5c17-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5c17-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5c17-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c17-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5c17-110">Requirements</span></span>  

 <span data-ttu-id="c5c17-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5c17-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c17-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5c17-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5c17-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c5c17-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5c17-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c17-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c17-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5c17-115">See also</span></span>

- [<span data-ttu-id="c5c17-116">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5c17-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="c5c17-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c5c17-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
