---
title: ICorDebugVariableSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e963e655c933c9191953bb32ba0b73adf0ae86d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774873"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="8aebd-102">ICorDebugVariableSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="8aebd-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="8aebd-103">Bir değişken boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="8aebd-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aebd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8aebd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aebd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8aebd-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="8aebd-106">Bir 32-bit işaretsiz tamsayı değişkeni içeren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8aebd-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8aebd-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8aebd-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8aebd-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8aebd-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aebd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8aebd-109">Requirements</span></span>  
 <span data-ttu-id="8aebd-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aebd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aebd-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8aebd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8aebd-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aebd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aebd-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aebd-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aebd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8aebd-114">See also</span></span>

- [<span data-ttu-id="8aebd-115">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aebd-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="8aebd-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8aebd-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
