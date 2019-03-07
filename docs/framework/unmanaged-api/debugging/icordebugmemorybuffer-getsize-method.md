---
title: ICorDebugMemoryBuffer::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fdf5e6e52b0c650e56368493074ea7db8e5bac9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485440"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="be39f-102">ICorDebugMemoryBuffer::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="be39f-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="be39f-103">Bellek arabellek boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="be39f-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be39f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be39f-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be39f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be39f-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="be39f-106">[out] Bellek arabellek boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be39f-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be39f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be39f-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be39f-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be39f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be39f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be39f-109">Requirements</span></span>  
 <span data-ttu-id="be39f-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be39f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be39f-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be39f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be39f-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be39f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be39f-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be39f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be39f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be39f-114">See also</span></span>
- [<span data-ttu-id="be39f-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be39f-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="be39f-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="be39f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
