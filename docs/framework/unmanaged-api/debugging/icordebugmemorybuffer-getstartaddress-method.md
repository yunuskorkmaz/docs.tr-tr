---
title: ICorDebugMemoryBuffer::GetStartAddress yöntemi
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aa816ea9e6185791e09bcdb0e47c50761a5ebc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422939"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="be0cf-102">ICorDebugMemoryBuffer::GetStartAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="be0cf-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="be0cf-103">Bellek arabelleği başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="be0cf-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be0cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be0cf-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be0cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be0cf-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="be0cf-106">[out] Bellek arabelleği başlangıç adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be0cf-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be0cf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be0cf-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="be0cf-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be0cf-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be0cf-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be0cf-109">Requirements</span></span>  
 <span data-ttu-id="be0cf-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be0cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be0cf-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be0cf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be0cf-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be0cf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be0cf-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be0cf-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be0cf-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be0cf-114">See Also</span></span>  
 [<span data-ttu-id="be0cf-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be0cf-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="be0cf-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="be0cf-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
