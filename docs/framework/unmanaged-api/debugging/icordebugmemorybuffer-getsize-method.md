---
title: ICorDebugMemoryBuffer::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0db104dbfa61b836aa01b99be45725ed4c04c798
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752786"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="022e2-102">ICorDebugMemoryBuffer::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="022e2-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="022e2-103">Bellek arabellek boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="022e2-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="022e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="022e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="022e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="022e2-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="022e2-106">[out] Bellek arabellek boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="022e2-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="022e2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="022e2-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="022e2-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="022e2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="022e2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="022e2-109">Requirements</span></span>  
 <span data-ttu-id="022e2-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="022e2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="022e2-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="022e2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="022e2-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="022e2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="022e2-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="022e2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="022e2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="022e2-114">See also</span></span>

- [<span data-ttu-id="022e2-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="022e2-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="022e2-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="022e2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
