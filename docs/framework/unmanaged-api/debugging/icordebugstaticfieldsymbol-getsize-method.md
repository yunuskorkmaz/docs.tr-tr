---
title: "ICorDebugStaticFieldSymbol::GetSize yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b67cbe6858e91e089c36047d6ed83743e45e1d1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="a2c00-102">ICorDebugStaticFieldSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2c00-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="a2c00-103">Statik alanının bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="a2c00-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c00-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2c00-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2c00-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2c00-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="a2c00-106">[out] Alanın uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a2c00-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2c00-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2c00-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2c00-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2c00-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c00-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2c00-109">Requirements</span></span>  
 <span data-ttu-id="a2c00-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c00-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c00-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2c00-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2c00-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2c00-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2c00-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c00-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c00-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2c00-114">See Also</span></span>  
 [<span data-ttu-id="a2c00-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2c00-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="a2c00-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a2c00-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
