---
title: ICorDebugMemoryBuffer::GetStartAddress yöntemi
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58649a0fc12ce63a1307af5d831dbf5e0d5a776a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136987"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="5783e-102">ICorDebugMemoryBuffer::GetStartAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="5783e-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="5783e-103">Bellek arabelleği başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="5783e-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5783e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5783e-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5783e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5783e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5783e-106">[out] Başlangıç adresi ara belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5783e-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5783e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5783e-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5783e-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5783e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5783e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5783e-109">Requirements</span></span>  
 <span data-ttu-id="5783e-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5783e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5783e-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5783e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5783e-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5783e-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5783e-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5783e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5783e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5783e-114">See also</span></span>

- [<span data-ttu-id="5783e-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5783e-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="5783e-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5783e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
