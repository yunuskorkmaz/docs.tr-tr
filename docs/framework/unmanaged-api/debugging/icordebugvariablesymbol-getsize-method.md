---
title: ICorDebugVariableSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027b3f773ff0ed0ca7bf9d193f97a3b060ea8494
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211848"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="290b3-102">ICorDebugVariableSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="290b3-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="290b3-103">Bir değişken boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="290b3-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="290b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="290b3-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="290b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="290b3-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="290b3-106">Bir 32-bit işaretsiz tamsayı değişkeni içeren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="290b3-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="290b3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="290b3-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="290b3-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="290b3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="290b3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="290b3-109">Requirements</span></span>  
 <span data-ttu-id="290b3-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="290b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="290b3-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="290b3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="290b3-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="290b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="290b3-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="290b3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="290b3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="290b3-114">See also</span></span>

- [<span data-ttu-id="290b3-115">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="290b3-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="290b3-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="290b3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
