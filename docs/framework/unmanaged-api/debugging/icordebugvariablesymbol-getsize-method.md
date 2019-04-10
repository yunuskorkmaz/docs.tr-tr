---
title: ICorDebugVariableSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027b3f773ff0ed0ca7bf9d193f97a3b060ea8494
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211848"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="af72a-102">ICorDebugVariableSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="af72a-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="af72a-103">Bir değişken boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="af72a-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af72a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af72a-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af72a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af72a-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="af72a-106">Bir 32-bit işaretsiz tamsayı değişkeni içeren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="af72a-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af72a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af72a-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af72a-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af72a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af72a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af72a-109">Requirements</span></span>  
 <span data-ttu-id="af72a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af72a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af72a-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af72a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af72a-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af72a-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="af72a-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="af72a-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af72a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af72a-114">See also</span></span>

- [<span data-ttu-id="af72a-115">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af72a-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="af72a-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="af72a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
