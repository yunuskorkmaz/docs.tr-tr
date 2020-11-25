---
title: 'ICorDebugVariableSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: 1079351e75ec9c48a9657f514ee56e2e6a4b0920
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731377"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="fbd18-102">ICorDebugVariableSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="fbd18-102">ICorDebugVariableSymbol::GetSize Method</span></span>

<span data-ttu-id="fbd18-103">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="fbd18-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd18-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fbd18-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbd18-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fbd18-105">Parameters</span></span>  

 `pcbValue`  
 <span data-ttu-id="fbd18-106">Değişkenin boyutunu içeren 32 bitlik işaretsiz tamsayıya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fbd18-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbd18-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fbd18-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbd18-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fbd18-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbd18-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fbd18-109">Requirements</span></span>  

 <span data-ttu-id="fbd18-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbd18-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbd18-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fbd18-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbd18-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fbd18-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbd18-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbd18-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbd18-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbd18-114">See also</span></span>

- [<span data-ttu-id="fbd18-115">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fbd18-115">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="fbd18-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fbd18-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
