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
ms.openlocfilehash: 256a15952cd52c5a096e1f0b8c7fc2086cde226c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="24dcf-102">ICorDebugStaticFieldSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="24dcf-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="24dcf-103">Statik alanının bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="24dcf-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24dcf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24dcf-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24dcf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24dcf-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="24dcf-106">[out] Alanın uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="24dcf-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24dcf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24dcf-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24dcf-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24dcf-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24dcf-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24dcf-109">Requirements</span></span>  
 <span data-ttu-id="24dcf-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24dcf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24dcf-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24dcf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24dcf-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24dcf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24dcf-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24dcf-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24dcf-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24dcf-114">See Also</span></span>  
 [<span data-ttu-id="24dcf-115">ICorDebugStaticFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="24dcf-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="24dcf-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="24dcf-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
