---
title: 'ICorDebugMemoryBuffer:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c88d389f80b4b3d811d95f65acd41f294d076b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969085"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="d439c-102">ICorDebugMemoryBuffer:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="d439c-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="d439c-103">Bellek arabelleğinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="d439c-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d439c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d439c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d439c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d439c-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="d439c-106">dışı Bellek arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d439c-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d439c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d439c-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d439c-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d439c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d439c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d439c-109">Requirements</span></span>  
 <span data-ttu-id="d439c-110">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d439c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d439c-111">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d439c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d439c-112">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d439c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d439c-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d439c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d439c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d439c-114">See also</span></span>

- [<span data-ttu-id="d439c-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d439c-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="d439c-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d439c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
