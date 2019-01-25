---
title: ICorDebugMemoryBuffer::GetSize yöntemi
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5984addb41c33468068f7ad24a15533f75dc367
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714730"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="a6555-102">ICorDebugMemoryBuffer::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6555-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="a6555-103">Bellek arabellek boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="a6555-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6555-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6555-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6555-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6555-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="a6555-106">[out] Bellek arabellek boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6555-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6555-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6555-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6555-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6555-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6555-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6555-109">Requirements</span></span>  
 <span data-ttu-id="a6555-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6555-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6555-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6555-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6555-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6555-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6555-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6555-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6555-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6555-114">See also</span></span>
- [<span data-ttu-id="a6555-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6555-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="a6555-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a6555-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
