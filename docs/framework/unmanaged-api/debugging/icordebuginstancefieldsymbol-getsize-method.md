---
title: 'Icordebugınstancefieldsymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: c4b193b45e30b0eba3367f18cb1e4c2b4e108fa8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724916"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="269f2-102">Icordebugınstancefieldsymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="269f2-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="269f2-103">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="269f2-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="269f2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="269f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="269f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="269f2-105">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="269f2-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="269f2-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="269f2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="269f2-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="269f2-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="269f2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="269f2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="269f2-109">Requirements</span></span>  

 <span data-ttu-id="269f2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="269f2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="269f2-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="269f2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="269f2-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="269f2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="269f2-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="269f2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269f2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="269f2-114">See also</span></span>

- [<span data-ttu-id="269f2-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="269f2-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="269f2-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="269f2-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
