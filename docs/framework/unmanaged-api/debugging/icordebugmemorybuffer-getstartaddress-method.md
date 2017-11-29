---
title: "ICorDebugMemoryBuffer::GetStartAddress yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97c08e87f63b36bfee5ade75e44f4867441bee92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="97bff-102">ICorDebugMemoryBuffer::GetStartAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="97bff-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="97bff-103">Bellek arabelleği başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="97bff-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97bff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97bff-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97bff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97bff-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="97bff-106">[out] Bellek arabelleği başlangıç adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97bff-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97bff-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97bff-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="97bff-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97bff-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97bff-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97bff-109">Requirements</span></span>  
 <span data-ttu-id="97bff-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97bff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97bff-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97bff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97bff-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97bff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97bff-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97bff-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97bff-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97bff-114">See Also</span></span>  
 [<span data-ttu-id="97bff-115">ICorDebugMemoryBuffer arabirimi</span><span class="sxs-lookup"><span data-stu-id="97bff-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="97bff-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="97bff-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
