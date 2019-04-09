---
title: ICorDebugStaticFieldSymbol::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9baa3632b6ede9ce45f34302611710344ed33761
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154329"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="7e820-102">ICorDebugStaticFieldSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e820-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="7e820-103">Boyutu bayt cinsinden statik alanı alır.</span><span class="sxs-lookup"><span data-stu-id="7e820-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e820-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e820-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e820-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e820-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="7e820-106">[out] Alanın uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7e820-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e820-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e820-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e820-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e820-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e820-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e820-109">Requirements</span></span>  
 <span data-ttu-id="7e820-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e820-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e820-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e820-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e820-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e820-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7e820-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7e820-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e820-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e820-114">See also</span></span>

- [<span data-ttu-id="7e820-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e820-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="7e820-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7e820-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
