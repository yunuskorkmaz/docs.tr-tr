---
title: "ICorDebugStaticFieldSymbol::GetAddress yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20c0c934772625d27057957d00e53fb4b485c4fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="5e938-102">ICorDebugStaticFieldSymbol::GetAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e938-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="5e938-103">Statik bir alana adresini alır.</span><span class="sxs-lookup"><span data-stu-id="5e938-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e938-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e938-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e938-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e938-105">Parameters</span></span>  
 <span data-ttu-id="5e938-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="5e938-106">pRVA</span></span>  
 <span data-ttu-id="5e938-107">[out] Statik alanının göreli sanal adres (RAV) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e938-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e938-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e938-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e938-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e938-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e938-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e938-110">Requirements</span></span>  
 <span data-ttu-id="5e938-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e938-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e938-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e938-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e938-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e938-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e938-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e938-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e938-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e938-115">See Also</span></span>  
 [<span data-ttu-id="5e938-116">ICorDebugStaticFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e938-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="5e938-117">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5e938-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
