---
title: 'ICorDebugMemoryBuffer:: GetStartAddress yöntemi'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: e2876398ceaf863bbb3c7e576d59b89c52f1bdaf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127982"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="bc56e-102">ICorDebugMemoryBuffer:: GetStartAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc56e-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="bc56e-103">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="bc56e-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc56e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc56e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc56e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc56e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="bc56e-106">dışı Bellek arabelleğinin başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc56e-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc56e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc56e-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="bc56e-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc56e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc56e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc56e-109">Requirements</span></span>  
 <span data-ttu-id="bc56e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc56e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc56e-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc56e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc56e-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bc56e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc56e-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc56e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc56e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc56e-114">See also</span></span>

- [<span data-ttu-id="bc56e-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc56e-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="bc56e-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bc56e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
