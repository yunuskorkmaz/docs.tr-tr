---
title: 'ICorDebugMemoryBuffer:: GetStartAddress yöntemi'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1394624051baa9e7dd21e29788d5fab28332081b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987556"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="6aab8-102">ICorDebugMemoryBuffer:: GetStartAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="6aab8-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="6aab8-103">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="6aab8-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aab8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6aab8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aab8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6aab8-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="6aab8-106">dışı Bellek arabelleğinin başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6aab8-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aab8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6aab8-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="6aab8-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6aab8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aab8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6aab8-109">Requirements</span></span>  
 <span data-ttu-id="6aab8-110">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aab8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aab8-111">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6aab8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6aab8-112">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6aab8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aab8-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aab8-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aab8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aab8-114">See also</span></span>

- [<span data-ttu-id="6aab8-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6aab8-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="6aab8-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6aab8-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
