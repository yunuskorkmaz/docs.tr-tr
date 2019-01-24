---
title: ICorDebugVariableSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a41ec4a556ca26404b5f76ddb35d9f73d7307a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659062"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="4c34b-102">ICorDebugVariableSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c34b-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="4c34b-103">Bir değişken boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="4c34b-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c34b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c34b-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c34b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c34b-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="4c34b-106">Bir 32-bit işaretsiz tamsayı değişkeni içeren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4c34b-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c34b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c34b-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c34b-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c34b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c34b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c34b-109">Requirements</span></span>  
 <span data-ttu-id="4c34b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c34b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c34b-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c34b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c34b-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c34b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c34b-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c34b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c34b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c34b-114">See also</span></span>
- [<span data-ttu-id="4c34b-115">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c34b-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="4c34b-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c34b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
